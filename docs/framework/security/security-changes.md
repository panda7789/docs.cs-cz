---
title: Změny zabezpečení v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204496"
---
# <a name="security-changes-in-the-net-framework"></a>Změny zabezpečení v rozhraní .NET Framework

Nejdůležitější změnou zabezpečení v .NET Framework 4,5 je vytváření silných názvů. Popis těchto změn najdete v tématu [Rozšířené silné pojmenování](../../standard/assembly/enhanced-strong-naming.md) .  
  
.NET Framework poskytuje model zabezpečení se dvěma vrstvami pro spravované aplikace. Aplikace Windows 8. x ze Storu běží v kontejneru zabezpečení systému Windows, který omezuje přístup k prostředkům. V rámci tohoto kontejneru běží spravované aplikace s plnou důvěryhodností. V perspektivě zabezpečení přístupu kódu (CAS) není k dispozici žádný vývojář, který by mohl zvýšit oprávnění. Informace o oprávněních udělených systémem Windows najdete v tématu [deklarace schopností aplikace (aplikace pro Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) na stránce Windows Dev Center. Informace o vytvoření aplikace Windows 8. x Store najdete v tématu [Vytvoření první aplikace pro C# Windows store pomocí nebo Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
