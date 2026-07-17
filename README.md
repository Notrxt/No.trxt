{
  "name": "noah-core",
  "version": "1.0.0",
  "description": "Enterprise backend for Roblox services",
  "author": "Notrxt",
  "license": "MIT",
  "private": true,
  "type": "module",
  "main": "dist/main.js",
  "scripts": {
    "dev": "tsx watch src/main.ts",
    "build": "tsc",
    "start": "node dist/main.js",
    "lint": "eslint .",
    "format": "prettier --write ."
  },
  "dependencies": {
    "@types/jsonwebtoken": "^9.0.6",
    "bcrypt": "^5.1.1",
    "compression": "^1.7.5",
    "cookie-parser": "^1.4.7",
    "cors": "^2.8.5",
    "dotenv": "^16.4.7",
    "express": "^4.21.2",
    "express-rate-limit": "^7.5.0",
    "helmet": "^8.0.0",
    "jsonwebtoken": "^9.0.2",
    "mongoose": "^8.10.1",
    "morgan": "^1.10.0",
    "pino": "^9.5.0",
    "redis": "^4.7.0",
    "uuid": "^11.0.5",
    "zod": "^3.24.1"
  },
  "devDependencies": {
    "@types/express": "^5.0.0",
    "@types/node": "^22.10.5",
    "eslint": "^9.17.0",
    "prettier": "^3.4.2",
    "tsx": "^4.19.2",
    "typescript": "^5.7.2"
  }
}import { Application } from "./app.js";

const application = new Application();

application.bootstrap().catch((error) => {
    console.error("[BOOTSTRAP_ERROR]", error);
    process.exit(1);
});texport class Environment {

    public static readonly PORT =
        Number(process.env.PORT ?? 3000);

    public static readonly NODE_ENV =
        process.env.NODE_ENV ?? "development";

    public static readonly DATABASE_URI =
        process.env.DATABASE_URI ?? "";

    public static readonly JWT_SECRET =
        process.env.JWT_SECRET ?? "";
export class Logger {

    private static timestamp(): string {

        return new Date().toISOString();

    }

    public static info(message: string): void {

        console.log(
            `[INFO] ${this.timestamp()} ${message}`
        );

    }

    public static warn(message: string): void {

        console.warn(
            `[WARN] ${this.timestamp()} ${message}`
        );

    }

    public static error(message: string): void {

        console.error(
            `[ERROR] ${this.timestamp()} ${message}`
        );

    }

    public static success(message: string): void {

        console.log(
            `[SUCCESS] ${this.timestamp()} ${message}`
        );

    }

}import { Router } from "express";

export class RouterProvider {

    public static routes(): Router {

        const router = Router();

        router.get(
            "/health",
            (_, response) => {

                response.status(200).json({

                    success: true,

                    application: "NoahCore",

                    version: "1.0.0",

                    timestamp: new Date().toISOString()

                });

            }
        );

        return router;

    }

}
}
