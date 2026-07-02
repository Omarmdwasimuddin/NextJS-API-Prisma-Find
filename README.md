## NextJS API---> Prisma Query Operations

### findMany() Operation
![](https://imgur.com/rgQI4cV.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findMany();

        return NextResponse.json(
            {status: "success", message: "Read data", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findMany() Where & Select Operation
![](https://imgur.com/fJHV7Ii.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findMany({
            where: {
                name: "Sayeed Anwar",
            },
            select: {
                id: false,
                name: false,
                designation: true,
                city: true,
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findMany() Search Operation
![](https://imgur.com/qaXKmlX.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.post.findMany({
            where: {
                content: {
                    contains: "Fifa"
                }
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findMany() orderBy Operation
![](https://imgur.com/I85n7DG.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findMany({
            orderBy: {
                // id: "asc"
                id: "desc"
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findMany() orderBy, skip, take Operaion
![](https://imgur.com/Mht3xOJ.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findMany({
            orderBy: {
                // id: "asc",
                id: "desc",
            },
            skip: 2,
            take: 3,
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findFirst() Operation
![](https://imgur.com/tkFUIJg.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findFirst();

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findFirst() orderBy, skip Operation
![](https://imgur.com/1zn7nHn.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findFirst({
            orderBy: {
                id: "desc"
            },
            skip: 1,
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findUnique() Operation
![](https://imgur.com/fxvJTwR.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findUnique({
            where: {
                id: "d86fd1e9-920e-49ee-9c4d-0907699aafc7",
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findMany() include relation Operation
![](https://imgur.com/gQ1BBkB.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.user.findMany({
            include: {
                posts: true,
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### findMany() select Operation
![](https://imgur.com/jEBiZdT.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.user.findMany({
            select: {
                id: true,
                name: true,
                email: true,
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---
