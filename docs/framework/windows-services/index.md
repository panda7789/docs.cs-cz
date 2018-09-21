---
title: Vývoj aplikací spouštěných jako služby systému Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: aa5e18f7e0ee1fc0836054b692872b18678106f3
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481725"
---
# <a name="develop-windows-service-apps"></a>Vývoj aplikací pro službu Windows

Pomocí sady Visual Studio nebo sady SDK rozhraní .NET Framework, můžete snadno vytvářet služby tak, že vytvoříte aplikaci, která je nainstalována jako služba. Tento typ aplikace se nazývá služby Windows. S funkcemi rozhraní framework můžete vytvářet služby, je, nainstalovat a spuštění, zastavení a jinak řídit jejich chování.

> [!NOTE]
> V sadě Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, která můžou spolupracovat s existujícího kódu C++, pokud je to nutné. Nebo můžete vytvořit službu Windows v nativním kódu C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).

## <a name="in-this-section"></a>V tomto oddílu

[Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

Poskytuje přehled aplikace služby Windows, dobu života služby a jak se liší od jiné běžné typy projektů aplikace služby.

[Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Poskytuje příklad vytvoření služby v jazyce Visual Basic a Visual C#.

[Architektura programování aplikace služby](../../../docs/framework/windows-services/service-application-programming-architecture.md)

Vysvětluje prvky jazyka, použít v service programování.

[Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)

Popisuje postup vytvoření a konfigurace služeb Windows pomocí šablony projektu služby Windows.

## <a name="related-sections"></a>Související oddíly

<xref:System.ServiceProcess.ServiceBase> – Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídu, která se používá k vytvoření služby.

<xref:System.ServiceProcess.ServiceProcessInstaller> – Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceInstaller> třídy k instalaci a odinstalaci služby.

<xref:System.ServiceProcess.ServiceInstaller> – Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídu, která se používá spolu s <xref:System.ServiceProcess.ServiceProcessInstaller> třídy k instalaci a odinstalaci služby.

[Vytvářet projekty ze šablon](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) -popisuje projekty typů použitých v této kapitole a jak si vybrat mezi nimi.
