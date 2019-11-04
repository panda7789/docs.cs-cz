---
title: 'Zmírnění rizika: kontroly středních cest'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457906"
---
# <a name="mitigation-path-colon-checks"></a>Zmírnění rizika: kontroly středních cest
Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu). Konkrétně jsou zkontrolovány správné syntaxe oddělovače jednotek (dvojtečka).  
  
## <a name="impact"></a>Dopad  
 Tyto změny blokují některé cesty identifikátorů URI, které byly dříve podporovány metodami <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>.  
  
## <a name="mitigation"></a>Zmírnění  
 Chcete-li se vyhnout problému dříve přijatelné cesty, která již není podporována <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>mi metodami, můžete provést následující akce:  
  
- Ručně odeberte schéma z adresy URL. Odeberte například `file://` z adresy URL.  
  
- Předejte identifikátor URI konstruktoru <xref:System.Uri> a načtěte hodnotu vlastnosti <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.  
  
- Odhlášení od nové normalizace cest nastavením `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> přepínač na `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
