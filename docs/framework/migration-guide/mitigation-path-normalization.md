---
title: 'Omezení rizik: Normalizace cesta'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37241dd666a5d10eeb35bcbb4c9e09a5bc56f620
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871502"
---
# <a name="mitigation-path-normalization"></a>Omezení rizik: Normalizace cesta
Počínaje aplikací cíl [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], došlo ke změně normalizace cestu v rozhraní .NET Framework.  
  
## <a name="what-is-path-normalization"></a>Co je cesta normalizace?  
 Normalizace cestu zahrnuje upravuje řetězec, který identifikuje cestu nebo soubor, který vyhovuje na platnou cestu na cílovém operačním systému. Normalizace obvykle zahrnuje:  
  
- Kanonizace oddělovače komponentu a adresáře.  
  
- Použití aktuální adresář pro relativní cestu.  
  
- Hodnocení relativní adresáře (`.`) nebo nadřazený adresář (`..`) v cestě.  
  
- Oříznutí zadané znaky.  
  
## <a name="the-changes"></a>Změny  
 Počínaje aplikací, které se zaměřují [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], došlo ke změně normalizace cesta následujícími způsoby:  
  
- Modul runtime odloží do operačního systému [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkce normalizace cesty.  
  
- Normalizace už zahrnuje ořezávání konec segmenty adresáře (například mezeru na konci názvu adresáře).  
  
- Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně `\\.\` a pro rozhraní API vstupně-výstupní operace souboru v mscorlib.dll, `\\?\`.  
  
- Modul runtime nelze ověřit zařízení syntaxe cesty.  
  
- Použití syntaxe zařízení pro přístup k alternativní datové proudy je podporované.  
  
## <a name="impact"></a>Dopad  
 Pro aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo později, tyto změny jsou standardně povoleny. By měl pomáhají zvýšit výkon při povolení metody pro přístup k dříve nedostupných cesty.  
  
 Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší verze, ale jsou spuštěna pod [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo později se tato změna nemá vliv.  
  
## <a name="mitigation"></a>Zmírnění  
 Aplikace, které cílí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete vyjádřit výslovný nesouhlas tuto změnu a použít starší verzi normalizace přidáním následujícího kódu do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 Aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo starší, ale jsou spuštěny na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nebo novější můžete povolit změny normalizace cestu tak, že přidáte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části aplikace. konfigurační soubor:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
