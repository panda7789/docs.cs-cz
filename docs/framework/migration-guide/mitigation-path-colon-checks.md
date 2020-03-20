---
title: 'Zmírnění: Kontrola dvojtečky cesty'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: c6e1106b6f5d8457417992941b9f28712d484442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181249"
---
# <a name="mitigation-path-colon-checks"></a>Zmírnění: Kontrola dvojtečky cesty
Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, byla provedena řada změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu). Zejména kontroly správné syntaxe oddělovače jednotky (dvojtečka) byly provedeny správnější.  
  
## <a name="impact"></a>Dopad  
 Tyto změny blokují některé <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> cesty URI a dříve podporované metody.  
  
## <a name="mitigation"></a>Omezení rizik  
 Chcete-li obejít problém dříve přijatelné cesty, která <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> již není podporována a metody, můžete provést následující kroky:  
  
- Ručně odeberte schéma z adresy URL. Můžete například `file://` odebrat z adresy URL.  
  
- Předajuridu uri konstruktoru <xref:System.Uri> a <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> načtěte hodnotu vlastnosti.  
  
- Odhlásit se z nové normalizace `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> cesty `true`nastavením přepínače na .  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
