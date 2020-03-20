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
ms.openlocfilehash: 61f969c22ac06bd6ed20ccfa9124db3bb35d0692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71053545"
---
# <a name="develop-windows-service-apps"></a>Vývoj servisních aplikací pro Windows

Pomocí sady Visual Studio nebo sady .NET Framework SDK můžete snadno vytvářet služby vytvořením aplikace, která je nainstalována jako služba. Tento typ aplikace se nazývá služba systému Windows. Pomocí funkcí architektury můžete vytvářet služby, instalovat je a spouštět, zastavovat a jinak řídit jejich chování.

> [!NOTE]
> V sadě Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce Visual C# nebo Visual Basic, který může v případě potřeby spolupracovat s existujícím kódem jazyka C++. Nebo můžete vytvořit službu systému Windows v nativním jazyce C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).

## <a name="in-this-section"></a>V tomto oddílu

[Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)

Poskytuje přehled aplikací služeb systému Windows, životnost služby a způsob, jakým se aplikace služby liší od jiných běžných typů projektů.

[Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Obsahuje příklad vytvoření služby v jazyce Visual Basic a Visual C#.

[Architektura programování aplikace služby](service-application-programming-architecture.md)

Vysvětluje jazykové prvky používané v programování služeb.

[Postupy: Vytváření služeb systému Windows](how-to-create-windows-services.md)

Popisuje proces vytváření a konfigurace služeb systému Windows pomocí šablony projektu služby systému Windows.

## <a name="related-sections"></a>Související oddíly

<xref:System.ServiceProcess.ServiceBase>- Popisuje hlavní rysy <xref:System.ServiceProcess.ServiceBase> třídy, která se používá k vytváření služeb.

<xref:System.ServiceProcess.ServiceProcessInstaller>- Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídy, která se používá <xref:System.ServiceProcess.ServiceInstaller> spolu s třídou k instalaci a odinstalaci služeb.

<xref:System.ServiceProcess.ServiceInstaller>- Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídy, která se používá <xref:System.ServiceProcess.ServiceProcessInstaller> spolu s třídou k instalaci a odinstalaci služby.

[Vytvořit projekty ze šablon](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) - Popisuje typy projektů použité v této kapitole a způsob jejich výběru.
