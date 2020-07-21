---
title: 'Zmírnění rizika: kontroly středních cest'
description: Přečtěte si o změnách provedených v .NET Framework 4.6.2 pro podporu kontrol správné syntaxe oddělovače jednotek (dvojtečka).
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: f32ee54f88bc4747fd0d8065b0dce06b151d1d9a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475447"
---
# <a name="mitigation-path-colon-checks"></a>Zmírnění rizika: kontroly středních cest
Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu). Konkrétně jsou zkontrolovány správné syntaxe oddělovače jednotek (dvojtečka).  
  
## <a name="impact"></a>Dopad  
 Tyto změny blokují některé cesty identifikátorů URI, které <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> dříve podporovaly metody a.  
  
## <a name="mitigation"></a>Omezení rizik  
 Chcete-li se vyhnout problému dříve přijatelné cesty, která již není podporována <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metodami a, můžete provést následující:  
  
- Ručně odeberte schéma z adresy URL. Například odeberte `file://` z adresy URL.  
  
- Předejte identifikátor URI <xref:System.Uri> konstruktoru a načtěte hodnotu <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> Vlastnosti.  
  
- Odhlášení od nové normalizace cest nastavením `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> přepínače na `true` .  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
