---
title: "Spuštění rozhraní .NET Framework 1.1 aplikace na Windows 8, Windows 8.1 nebo Windows 10"
ms.custom: 
ms.date: 05/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d5b99390e62984b37b0d7267c40b1221f556f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Spuštění rozhraní .NET Framework 1.1 aplikace na Windows 8, Windows 8.1 nebo Windows 10

Nepodporuje rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo operační systémy Windows 10. V některých případech je rozhraní .NET Framework 1.1 konkrétně identifikovat podle potřeby pro aplikaci, ke spuštění. V těchto případech, měli byste požádat vašeho nezávislý dodavatel softwaru (ISV) tak, aby měl aplikaci upgradovat ke spuštění na [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] nebo novější verze. Další informace najdete v tématu [migrace z verze rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Nainstalujte rozhraní .NET Framework 1.1 z disku CD nebo stažení softwaru společnosti Microsoft

Není možné ručně nainstalovat rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo Windows 10. Už se nepodporuje. Pokud se pokusíte nainstalovat balíček, zobrazí se následující chybová zpráva: "Instalační program nemůže pokračovat, protože tato verze rozhraní .NET Framework je kompatibilní s dříve nainstalované jeden." Chcete-li tento problém vyřešit, nainstalujte [rozhraní .NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22). Tato verze zahrnuje rozhraní .NET Framework 2.0 (verze, která následuje rozhraní .NET Framework 1.1), který není podporován na [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]a Windows 10. Musí se vždy pokusí nainstalovat aplikaci nejprve k určení, pokud ho se automaticky aktualizují na novější verzi rozhraní .NET Framework. Pokud ne, obraťte se na vaše ISV pro aktualizaci aplikace.

## <a name="see-also"></a>Viz také

[Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[instalaci rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
