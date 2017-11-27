---
title: "Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba734dd3a9585b52b96cb2d27743da6190961126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a>Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework
Nainstalované aktualizace pro jednotlivé verze rozhraní .NET Framework nainstalované v počítači jsou uvedeny v registru systému Windows. Chcete-li zobrazit tyto informace, můžete použít editor registru (regedit.exe).  
  
 V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích. Informace o zjišťování čísla nainstalovaná verze najdete v tématu [postupy: určení rozhraní .NET Framework verze jsou nainstalované](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Informace o instalaci rozhraní .NET Framework najdete v tématu [instalaci rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).  
  
### <a name="to-find-installed-updates"></a>Vyhledání nainstalovaných aktualizací  
  
1.  Otevřete program **regedit.exe**. V systému Windows 8 a vyšší otevření obrazovky Start a zadejte název. V dřívějších verzích systému Windows na **spustit** nabídce zvolte **spustit** a pak na **otevřete** zadejte **regedit.exe**.  
  
     Ke spuštění souboru regedit.exe musíte mít oprávnění správce.  
  
2.  V editoru registru otevřete následující podklíč:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates  
  
     Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují. Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).  
  
## <a name="example"></a>Příklad  
 Následující kód programově určuje aktualizace rozhraní .NET Framework, které jsou v počítači nainstalovány. Chcete-li spustit tento příklad, musíte mít pověření správce.  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)]
 [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 Vzorové postupy budou mít výstup podobný následujícímu:  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a>Viz také

[Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[Instalace rozhraní .NET Framework](../../../docs/framework/install/guide-for-developers.md)   
[Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)
