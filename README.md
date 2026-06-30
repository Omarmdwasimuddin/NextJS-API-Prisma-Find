## NextJS-API-Prisma-Find

### findMany Operation
![](https://imgur.com/rgQI4cV.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function POST(request: NextRequest) {
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
