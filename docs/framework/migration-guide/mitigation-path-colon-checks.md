---
title: 'Omezení rizik: Path Colon Checks'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 741bb73280d9e81fc1865867152ab1243e9dd53c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494675"
---
# <a name="mitigation-path-colon-checks"></a>Omezení rizik: Path Colon Checks
Počínaje aplikací, které se zaměřují [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], počet změn byly provedeny na podporu dříve nepodporované cesty (jak z hlediska délku a formátu). Konkrétně kontroly syntaxe správná jednotka oddělovač (dvojtečka) byly provedeny více správné.  
  
## <a name="impact"></a>Dopad  
 Tyto změny blokovat některé cesty identifikátoru URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody dříve podporovány.  
  
## <a name="mitigation"></a>Zmírnění  
 Chcete-li vyřešit problém dříve přijatelné cestu, která je již nejsou podporovány <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, můžete provádět následující:  
  
-   Schéma ručně odeberte z adresy URL. Například odebrat `file://` z adresy URL.  
  
-   Předat identifikátor URI <xref:System.Uri> konstruktoru a načtení hodnoty <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> vlastnost.  
  
-   Vyjádřit výslovný nesouhlas nové normalizace cestu tak, že nastavíte `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> přepnout na `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
