---
title: Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 507de3ca635986d1f4e0e3ba7c607a4af774cdcf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716266"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10

.NET Framework 1,1 není podporován v systémech Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 ani v operačních systémech Windows 10. V některých případech je .NET Framework 1,1 specificky identifikována jako požadovaná pro spuštění aplikace. V těchto případech byste se měli obrátit na nezávislého výrobce softwaru (ISV), aby se aplikace upgradovala, aby běžela v .NET Framework 3,5 SP1 nebo novější verzi. Další informace najdete v tématu [migrace z .NET Framework 1,1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Instalace .NET Framework 1,1 z disku CD nebo stažení softwaru

Nelze ručně nainstalovat .NET Framework 1,1 ve Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 nebo Windows 10. Již není podporován. Pokud se pokusíte nainstalovat balíček, zobrazí se následující chybová zpráva: "instalace nemůže pokračovat, protože tato verze .NET Framework není kompatibilní s dříve nainstalovanou." Chcete-li tento problém vyřešit, nainstalujte [.NET Framework 3,5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Tato verze zahrnuje .NET Framework 2,0 (verze, která následuje .NET Framework 1,1), která je podporovaná ve Windows 8, Windows 8.1 a Windows 10. Vždy byste se měli nejdřív pokusit nainstalovat aplikaci, abyste zjistili, jestli bude automaticky aktualizována na novější verzi .NET Framework. Pokud ne, obraťte se na svého nezávislého výrobce softwaru pro aktualizaci aplikace.

## <a name="see-also"></a>Viz také:

- [Migrace z rozhraní .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](dotnet-35-windows-10.md)
