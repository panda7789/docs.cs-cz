---
title: Spuštění rozhraní .NET Framework 1.1 aplikací pro Windows 8, Windows 8.1 nebo Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ceaa3ea9d9140c6b5df45f067558da2de80b8dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535408"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Spuštění rozhraní .NET Framework 1.1 aplikací pro Windows 8, Windows 8.1 nebo Windows 10

Rozhraní .NET Framework 1.1 není podporován [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo operační systémy Windows 10. V některých případech se rozhraní .NET Framework 1.1 je určeno pro spouštění aplikace podle potřeby. V takových případech by kontaktovat svého nezávislého dodavatele softwaru (ISV), aby upgradovali na spuštění v aplikaci [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] nebo vyšší verze. Další informace najdete v tématu [migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Instalace rozhraní .NET Framework 1.1 z disku CD nebo stažení softwaru

Není možné nainstalovat ručně rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo Windows 10. Se už nepodporuje. Pokud se pokusíte nainstalovat balíček, zobrazí se následující chybová zpráva: "Instalace nemůže pokračovat, protože tato verze rozhraní .NET Framework není kompatibilní s dříve nainstalovanou." Chcete-li tento problém vyřešit, nainstalujte [rozhraní .NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Tato verze zahrnuje rozhraní .NET Framework 2.0 (verze následující po verzi rozhraní .NET Framework 1.1), který není podporovaný na [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]a Windows 10. Musí se vždy pokusí nainstalovat aplikaci, abyste mohli určit, pokud je automaticky aktualizována na novější verzi rozhraní .NET Framework. Pokud tomu tak není, požádejte svého prodejce softwaru o aktualizaci aplikace.

## <a name="see-also"></a>Viz také:

- [Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
