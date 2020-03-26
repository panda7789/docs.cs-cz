---
title: Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10
description: Popisuje, jak přizpůsobit aplikace, které vyžadují rozhraní .NET Framework 1.1, které již nejsou podporovány v mnoha verzích operačního systému Windows.
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 6d1cb2f9251bba96d0a378bf4dbab9f7da267037
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111787"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10

Rozhraní .NET Framework 1.1 není podporováno v operačních systémech Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 nebo Windows 10. V některých případech je pro spuštění aplikace vyžadována rozhraní .NET Framework 1.1. V těchto případech se obraťte na nezávislého dodavatele softwaru (ISV) a požádejte o upgrade aplikace na rozhraní .NET Framework 3.5 SP1 nebo novější verzi. Další informace naleznete [v tématu Migrace z rozhraní .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-net-framework-11-from-a-cd-or-download-center"></a>Instalace rozhraní .NET Framework 1.1 z disku CD nebo download centra

Rozhraní .NET Framework 1.1 ve Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 nebo Windows 10 není možné ručně nainstalovat z disku CD nebo download centra. Už není podporována. Pokud se pokusíte nainstalovat balíček, zobrazí se následující chybová zpráva: "Instalační program nemůže pokračovat, protože tato verze rozhraní .NET Framework není kompatibilní s dříve nainstalovanou verzí." Chcete-li tento problém vyřešit, nainstalujte [rozhraní .NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Tato verze obsahuje rozhraní .NET Framework 2.0 (následující verzi rozhraní .NET Framework 1.1), která je podporována ve Windows 8, Windows 8.1 a Windows 10. Vždy byste se měli nejprve pokusit nainstalovat aplikaci, abyste zjistili, zda bude automaticky aktualizována na novější verzi rozhraní .NET Framework. Pokud tomu tak není, požádejte svého isva o aktualizaci aplikace.

## <a name="see-also"></a>Viz také

- [Migrace z rozhraní .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](dotnet-35-windows-10.md)
