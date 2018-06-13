---
title: 'Omezení rizik: Cesta normalizaci'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36433dcce1e47b329f5407e86ce3923a44cb6444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389505"
---
# <a name="mitigation-path-normalization"></a>Omezení rizik: Cesta normalizaci
Počínaje aplikací cíl [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], došlo ke změně cesty normalizace v rozhraní .NET Framework.  
  
## <a name="what-is-path-normalization"></a>Co je cesta normalizaci?  
 Normalizace cestu zahrnuje úprava řetězec, který identifikuje cesta nebo soubor, který vyhovuje na cestu na cílovém operačním systému. Normalizaci obvykle zahrnuje:  
  
-   Kanonizace oddělovače součásti a adresář.  
  
-   Použití aktuálního adresáře na relativní cestu.  
  
-   Vyhodnocení adresáři relativní (`.`) nebo nadřazený adresář (`..`) v cestě.  
  
-   Oříznutí zadané znaky.  
  
## <a name="the-changes"></a>Změny  
 Počínaje aplikací cílených [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cesta normalizaci došlo ke změně následujícími způsoby:  
  
-   Modul runtime odkládat údaje v operačním systému [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) funkce, která má normalizuje cesty.  
  
-   Už normalizace zahrnuje ořezávání konec directory segmenty (například mezeru na konci názvu adresáře).  
  
-   Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně `\\.\` a pro soubor vstupně-výstupních operací rozhraní API v mscorlib.dll, `\\?\`.  
  
-   Modul runtime neověřuje zařízení syntaxe cesty.  
  
-   Použití syntaxe zařízení pro přístup k alternativní datové proudy je podporováno.  
  
## <a name="impact"></a>Dopad  
 Pro aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější, jsou tyto změny na ve výchozím nastavení. Jejich měli zlepšit výkon při povolení metody pro přístup k dřív nepřístupný cesty.  
  
 Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší verze, ale jsou spuštěno [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější se tato změna nemá vliv.  
  
## <a name="mitigation"></a>Zmírnění  
 Aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete zamítnutí této změny a použít starší verzi normalizace přidáním následujícího [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddíl konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo starší ale běží na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete povolit změny cesty normalizaci přidáním následující řádek do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část aplikace. konfigurační soubor:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
