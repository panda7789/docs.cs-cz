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
ms.openlocfilehash: 84e80b99ee6d872714180e73354d20770c21e144
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400078"
---
# <a name="security-changes-in-the-net-framework"></a>Změny zabezpečení v rozhraní .NET Framework
Nejdůležitější změny zabezpečení v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] v silné názvy. V tématu [rozšířené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md) popis tyto změny.  
  
 Rozhraní .NET Framework poskytuje model zabezpečení dvouvrstvá pro spravované aplikace. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace běžet v kontejneru zabezpečení systému Windows, která omezuje přístup k prostředkům. V rámci kontejneru spusťte plně důvěryhodný pro spravované aplikace. Z hlediska zabezpečení (CA) kód přístup není nic, které vývojář může provádět o zvýšení oprávnění. Informace o oprávnění udělují Windows najdete v tématu [deklarace funkce aplikace (aplikace pro Windows Store)](http://go.microsoft.com/fwlink/?LinkId=230436) ve službě Windows Dev Center. Informace o vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v části [vytvoření první aplikace Windows Store pomocí jazyka C# nebo Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).
