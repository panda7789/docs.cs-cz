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
ms.openlocfilehash: 61f9e68bcc554dc3e4a4878e575d3f046a8ef9f5
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378590"
---
# <a name="security-changes-in-the-net-framework"></a>Změny zabezpečení v rozhraní .NET Framework
Nejdůležitější změny zabezpečení v rozhraní .NET Framework 4.5 je v silné názvy. Zobrazit [vylepšené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md) popis těchto změn.  
  
 Rozhraní .NET Framework poskytuje model zabezpečení dvouvrstvé pro spravované aplikace. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] spuštění aplikace v kontejneru Windows zabezpečení, která omezuje přístup k prostředkům. V rámci kontejneru spusťte spravované aplikace plně důvěryhodná. Z hlediska kódu access security (CAS) není nic, co Vývojář můžete udělat ke zvýšení oprávnění. Informace o oprávněních udělených systémem Windows, naleznete v tématu [deklarace funkcí aplikace (aplikace pro Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) Windows Dev Center. Informace o vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v článku [vytvoření první aplikace pro Windows Store pomocí jazyka C# nebo Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
