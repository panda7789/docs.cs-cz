---
title: .NET Framework požadavky na systém
description: Zjistěte, jaký je hardware, operační systém a požadavky na software pro instalaci .NET Framework 4,5 a novějších verzí.
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bed0084fd576ba9b9f9eeb51e9e2466938e43490
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106513"
---
# <a name="net-framework-system-requirements"></a>.NET Framework požadavky na systém

Tabulky v tomto tématu poskytují požadavky na hardware, operační systém a software pro následující verze .NET Framework:

- .NET Framework 4,5 a jeho vydání bodů (4.5.1 a 4.5.2).
- .NET Framework 4,6 a jeho vydání bodů (4.6.1 a 4.6.2).
- .NET Framework 4,7 a jeho vydání bodů (4.7.1 a 4.7.2).
- .NET Framework 4,8

Informace o .NET Framework verzích starších než .NET Framework 4,5 najdete v tématu [.NET Framework verzích a závislostí](../migration-guide/versions-and-dependencies.md).

Vývojová prostředí, která umožňují vyvíjet aplikace pro .NET Framework mají samostatnou sadu požadavků.

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

Informace o stažení a odkazy najdete v tématu [instalace .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).

Informace o životním cyklu podpory verze .NET Framework najdete v tématu [životní cyklus podpora Microsoftu](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Hardwarové požadavky

|                          |        |
| ------------------------ | ------ |
| **Mobilních**            | 1 GHz  |
| **SRAM**                  | 512 MB |
| **Místo na disku (minimální)** |        |
| 32bitová                   | 4,5 GB |
| 64bitová                   | 4,5 GB |

## <a name="installation-requirements"></a>Požadavky na instalaci

.NET Framework vyžaduje k instalaci oprávnění správce. Pokud nemáte práva správce k počítači, do kterého chcete nainstalovat .NET Framework, obraťte se na správce sítě.

## <a name="supported-client-operating-systems"></a>Podporované klientské operační systémy

| Operační systém | Podporované edice | Předinstalované s operačním systémem | Instalovatelné samostatně |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows 10 Květen 2019 Update | 32-bit a 64-bit | .NET Framework 4,8 | -- |
| Windows 10 říjen 2018 – aktualizace | 32-bit a 64-bit | .NET Framework 4.7.2 | .NET Framework 4,8 |
| Aktualizace Windows 10. dubna 2018 | 32-bit a 64-bit | .NET Framework 4.7.2 |.NET Framework 4,8|
| Aktualizace Creators v systému Windows 10 | 32-bit a 64-bit | .NET Framework 4.7.1 | .NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| Windows 10 Creators Update | 32-bit a 64-bit | Rozhraní .NET framework 4.7 | .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| Windows 10 Anniversary Update | 32-bit a 64-bit | .NET Framework 4.6.2 |Rozhraní .NET framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8  |
| Listopadová aktualizace pro Windows 10 | 32-bit a 64-bit | .NET Framework 4.6.1 | .NET Framework 4.6.2 |
| Windows 10 | 32-bit a 64-bit | .NET Framework 4.6 | .NET Framework 4.6.1 <br/><br/> .NET Framework 4.6.2 |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32 bitů, 64 bitů a ARM | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />Rozhraní .NET framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32 bitů, 64 bitů a ARM | .NET Framework 4.5 | .NET Framework 4.5.1<br /><br />.NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1 |
| Windows 7 SP1|32-bit a 64-bit | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />Rozhraní .NET framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| Windows Vista SP2|32-bit a 64-bit | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |
| Windows XP |32-bit a 64-bit | -- | .NET Framework 4 |

 **Poznámky:**

- V systémech Windows 7 .NET Framework vyžaduje systém Windows 7 SP1. Pokud jste v systému Windows 7 a ještě jste nenainstalovali aktualizaci Service Pack 1, musíte to provést před instalací .NET Framework.

- .NET Framework 4,5 se podporuje v Windows Preinstallation Environment (Windows PE). V systému Windows PE nejsou podporovány všechny funkce.

- .NET Framework 4 také podporuje platformu IA64.

- U všech platforem doporučujeme upgradovat na nejnovější aktualizaci Service Pack systému Windows a nainstalovat důležité aktualizace, které jsou k dispozici na [webu Web Windows Update](https://go.microsoft.com/fwlink/?LinkId=168461) , aby se zajistila nejlepší kompatibilita a zabezpečení.

- V 64 operačních systémech podporuje .NET Framework rozhraní WOW64 (32-bit Processing v počítači s 64) a | nativní zpracování 64.

## <a name="supported-server-operating-systems"></a>Podporované serverové operační systémy

| Operační systém | Podporované edice | Předinstalované s operačním systémem | Instalovatelné samostatně |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server. 2019 | 64bitová | .NET Framework 4.7.2 | .NET Framework 4,8 |
| Windows Server verze 1809 | 64bitová | .NET Framework 4.7.2 | .NET Framework 4,8 |
| Windows Server verze 1803 | 64bitová | .NET Framework 4.7.2 | .NET Framework 4,8 |
| Windows Server verze 1709 | 64bitová | .NET Framework 4.7.1 | .NET Framework 4.7.2|
| Windows Server 2016 | 64bitová | .NET Framework 4.6.2 | Rozhraní .NET framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| Windows Server 2012 R2 | 64bitová | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />Rozhraní .NET framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| Windows Server 2012 (64-bit Edition) | 64bitová| .NET Framework 4.5 | .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />Rozhraní .NET framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| Windows Server 2008 R2 SP1|64bitová | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />Rozhraní .NET framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4,8 |
| Windows Server 2008 SP2|32-bit a 64-bit | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |

 **Poznámky:**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]zahrnuje .NET Framework 4,5, takže je nemusíte instalovat samostatně. [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] Podobně zahrnuje .NET Framework 4.5.1.

- .NET Framework má omezené podpory pro roli jádra serveru s Windows Serverem 2008 R2 SP1 nebo novějším. Seznam nepodporovaných rozhraní API najdete v tématu [funkce jádra serveru .NET](https://docs.microsoft.com/previous-versions//dd745015(v=vs.85)) .

- .NET Framework není podporován v systémech Windows Server 2008 R2 pro počítače s procesorem Itanium.

- V systému Windows Server 2008 SP2 není .NET Framework v roli jádro serveru podporováno.

- U všech platforem doporučujeme upgradovat na nejnovější aktualizaci Service Pack systému Windows a důležité aktualizace, které jsou k dispozici na [webu Web Windows Update](https://go.microsoft.com/fwlink/?LinkId=168461) , aby se zajistila nejvyšší kompatibilita a zabezpečení. V některých operačních systémech může být nutné nainstalovat nejnovější aktualizaci Service Pack systému Windows.

- V 64 operačních systémech podporuje .NET Framework rozhraní WOW64 (32-bit Processing v počítači s 64) a 64 nativní 16bitové zpracování.

## <a name="see-also"></a>Viz také:

- [Průvodce instalací](../../../docs/framework/install/index.md)
- [Začínáme](../../../docs/framework/get-started/index.md)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
