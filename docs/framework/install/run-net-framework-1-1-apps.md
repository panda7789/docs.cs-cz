---
title: Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ad78c9a277af23eebe357ef986ea59d16bb444e
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833739"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Spouštění aplikací využívajících .NET Framework 1.1 v systému Windows 8, Windows 8.1 nebo Windows 10

Rozhraní .NET Framework 1.1 není podporován [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo operační systémy Windows 10. V některých případech se rozhraní .NET Framework 1.1 je určeno pro spouštění aplikace podle potřeby. V takových případech by kontaktovat svého nezávislého dodavatele softwaru (ISV), aby upgradovali na spuštění v rozhraní .NET Framework 3.5 SP1 nebo novější verze aplikace. Další informace najdete v tématu [migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Instalace rozhraní .NET Framework 1.1 z disku CD nebo stažení softwaru

Není možné nainstalovat ručně rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo Windows 10. Se už nepodporuje. Pokud se pokusíte nainstalovat balíček, zobrazí se následující chybová zpráva: "Instalace nemůže pokračovat, protože tato verze rozhraní .NET Framework není kompatibilní s dříve nainstalovanou." Chcete-li tento problém vyřešit, nainstalujte [rozhraní .NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Tato verze zahrnuje rozhraní .NET Framework 2.0 (verze následující po verzi rozhraní .NET Framework 1.1), který není podporovaný na [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]a Windows 10. Musí se vždy pokusí nainstalovat aplikaci, abyste mohli určit, pokud je automaticky aktualizována na novější verzi rozhraní .NET Framework. Pokud tomu tak není, požádejte svého prodejce softwaru o aktualizaci aplikace.

## <a name="see-also"></a>Viz také:

- [Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
