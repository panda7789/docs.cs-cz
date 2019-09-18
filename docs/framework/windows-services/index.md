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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053545"
---
# <a name="develop-windows-service-apps"></a>Vývoj aplikací služby systému Windows

Pomocí sady Visual Studio nebo sady .NET Framework SDK můžete snadno vytvářet služby vytvořením aplikace, která je nainstalovaná jako služba. Tento typ aplikace se nazývá služba systému Windows. S funkcemi architektury můžete vytvářet služby, instalovat je a spouštět, zastavovat a jinak řídit jejich chování.

> [!NOTE]
> V aplikaci Visual Studio můžete vytvořit službu ve spravovaném kódu v jazyce C# Visual nebo Visual Basic, která může v případě potřeby C++ spolupracovat s existujícím kódem. Nebo můžete vytvořit službu systému Windows v nativním režimu C++ pomocí [Průvodce projektem ATL](/cpp/atl/reference/atl-project-wizard).

## <a name="in-this-section"></a>V tomto oddílu

[Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)

Poskytuje přehled aplikací služby systému Windows, životnosti služby a způsobu, jakým se aplikace služby liší od jiných běžných typů projektů.

[Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

V této části najdete příklad vytvoření služby v Visual Basic a vizuálu C#.

[Architektura programování aplikace služby](service-application-programming-architecture.md)

Vysvětluje prvky jazyka používané při programování služeb.

[Postupy: Vytvořit služby systému Windows](how-to-create-windows-services.md)

Popisuje proces vytváření a konfigurace služeb systému Windows pomocí šablony projektu služby systému Windows.

## <a name="related-sections"></a>Související oddíly

<xref:System.ServiceProcess.ServiceBase>– Popisuje hlavní funkce <xref:System.ServiceProcess.ServiceBase> třídy, které slouží k vytváření služeb.

<xref:System.ServiceProcess.ServiceProcessInstaller>– Popisuje funkce <xref:System.ServiceProcess.ServiceProcessInstaller> třídy, které se používají spolu <xref:System.ServiceProcess.ServiceInstaller> s třídou pro instalaci a odinstalaci služeb.

<xref:System.ServiceProcess.ServiceInstaller>– Popisuje funkce <xref:System.ServiceProcess.ServiceInstaller> třídy, která se používá společně <xref:System.ServiceProcess.ServiceProcessInstaller> s třídou pro instalaci a odinstalaci vaší služby.

[Vytváření projektů z šablon](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) – popisuje typy projektů používané v této kapitole a jejich výběr.
