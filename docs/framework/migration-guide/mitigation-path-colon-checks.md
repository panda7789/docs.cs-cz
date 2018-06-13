---
title: 'Omezení rizik: Cesta dvojtečkou kontroly'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a54220a90a5120d13c89232d30ab40140c324097
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387377"
---
# <a name="mitigation-path-colon-checks"></a>Omezení rizik: Cesta dvojtečkou kontroly
Počínaje aplikací cílených [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], počet změn, byly provedeny na podporu dříve nepodporované cesty (jak z hlediska délku a format). Konkrétně byly provedeny kontroly syntaxe oddělovače správné jednotky (dvojtečkou) více správné.  
  
## <a name="impact"></a>Dopad  
 Tyto změny blokovat některé cesty identifikátoru URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody dřív podporované.  
  
## <a name="mitigation"></a>Zmírnění  
 Chcete-li vyřešit problém dříve přijatelné cestu, která se už nepodporuje <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metod, můžete provést následující:  
  
-   Schéma ručně odeberte z adresy URL. Například odebrat `file://` z adresy URL.  
  
-   Identifikátor URI pro předávání <xref:System.Uri> konstruktoru a načíst hodnotu <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> vlastnost.  
  
-   Vyjádření výslovného nesouhlasu s novou cestu normalizaci nastavením `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> přepnout `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
