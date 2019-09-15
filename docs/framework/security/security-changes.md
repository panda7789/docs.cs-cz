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
ms.openlocfilehash: bfc48d4fed127b288353f0295f2de1ca33e0a8fe
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971215"
---
# <a name="security-changes-in-the-net-framework"></a>Změny zabezpečení v rozhraní .NET Framework
Nejdůležitější změnou zabezpečení v .NET Framework 4,5 je vytváření silných názvů. Popis těchto změn najdete v tématu [Rozšířené silné pojmenování](../../standard/assembly/enhanced-strong-naming.md) .  
  
 .NET Framework poskytuje model zabezpečení se dvěma vrstvami pro spravované aplikace. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikace běží v kontejneru zabezpečení systému Windows, který omezuje přístup k prostředkům. V rámci tohoto kontejneru běží spravované aplikace s plnou důvěryhodností. V perspektivě zabezpečení přístupu kódu (CAS) není k dispozici žádný vývojář, který by mohl zvýšit oprávnění. Informace o oprávněních udělených systémem Windows najdete v tématu [deklarace schopností aplikace (aplikace pro Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) na stránce Windows Dev Center. Informace o vytvoření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace najdete v tématu [Vytvoření první aplikace pro Windows Store pomocí C# nebo Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
