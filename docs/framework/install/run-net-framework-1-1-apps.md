---
title: Spuštění rozhraní .NET Framework 1.1 aplikace na Windows 8, Windows 8.1 nebo Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b234d4e2fe7d5efe0a6c33f61b9ba422b55803d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386454"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Spuštění rozhraní .NET Framework 1.1 aplikace na Windows 8, Windows 8.1 nebo Windows 10

Nepodporuje rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo operační systémy Windows 10. V některých případech je rozhraní .NET Framework 1.1 konkrétně identifikovat podle potřeby pro aplikaci, ke spuštění. V těchto případech, měli byste požádat vašeho nezávislý dodavatel softwaru (ISV) tak, aby měl aplikaci upgradovat ke spuštění na [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] nebo novější verze. Další informace najdete v tématu [migrace z verze rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Nainstalujte rozhraní .NET Framework 1.1 z disku CD nebo stažení softwaru společnosti Microsoft

Není možné ručně nainstalovat rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo Windows 10. Už se nepodporuje. Pokud se pokusíte nainstalovat balíček, zobrazí se následující chybová zpráva: "Instalační program nemůže pokračovat, protože tato verze rozhraní .NET Framework je kompatibilní s dříve nainstalované jeden." Chcete-li tento problém vyřešit, nainstalujte [rozhraní .NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22). Tato verze zahrnuje rozhraní .NET Framework 2.0 (verze, která následuje rozhraní .NET Framework 1.1), který není podporován na [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]a Windows 10. Musí se vždy pokusí nainstalovat aplikaci nejprve k určení, pokud ho se automaticky aktualizují na novější verzi rozhraní .NET Framework. Pokud ne, obraťte se na vaše ISV pro aktualizaci aplikace.

## <a name="see-also"></a>Viz také

[Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[instalaci rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
