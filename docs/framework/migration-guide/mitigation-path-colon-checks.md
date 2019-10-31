---
title: 'Zmírnění rizika: kontroly středních cest'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: ee71f6ef1e70509e772aee2cc75d00c33122a92e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126222"
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

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6-2.md)
