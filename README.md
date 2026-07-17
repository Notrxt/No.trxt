
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
