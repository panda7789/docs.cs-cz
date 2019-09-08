---
title: Zmírnění Kontroly dvojtečky cest
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a74c25a9bf4dd8b9ab86bd280881fe1a7999e1d5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789994"
---
# <a name="mitigation-path-colon-checks"></a>Zmírnění Kontroly dvojtečky cest
Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu). Konkrétně jsou zkontrolovány správné syntaxe oddělovače jednotek (dvojtečka).  
  
## <a name="impact"></a>Dopad  
 Tyto změny blokují některé cesty identifikátorů <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> URI <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> , které dříve podporovaly metody a.  
  
## <a name="mitigation"></a>Zmírnění  
 Chcete-li se vyhnout problému dříve přijatelné cesty, která již není podporována <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> metodami a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> , můžete provést následující:  
  
- Ručně odeberte schéma z adresy URL. Například odeberte `file://` z adresy URL.  
  
- Předejte identifikátor URI <xref:System.Uri> konstruktoru a načtěte hodnotu <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> vlastnosti.  
  
- Odhlášení od nové normalizace `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> cest nastavením přepínače na `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6-2.md)
