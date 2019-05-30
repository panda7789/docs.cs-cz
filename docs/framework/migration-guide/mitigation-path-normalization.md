---
title: 'Omezení rizik: Normalizace cesta'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1c704113c8e05e493cdb3ef24f6376ab54b1cb
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251117"
---
# <a name="mitigation-path-normalization"></a>Omezení rizik: Normalizace cesta
Počínaje aplikací cílového rozhraní .NET Framework 4.6.2, cesta normalizace v rozhraní .NET Framework byl změněn.  
  
## <a name="what-is-path-normalization"></a>Co je cesta normalizace?  
 Normalizace cestu zahrnuje upravuje řetězec, který identifikuje cestu nebo soubor, který vyhovuje na platnou cestu na cílovém operačním systému. Normalizace obvykle zahrnuje:  
  
- Kanonizace oddělovače komponentu a adresáře.  
  
- Použití aktuální adresář pro relativní cestu.  
  
- Hodnocení relativní adresáře (`.`) nebo nadřazený adresář (`..`) v cestě.  
  
- Oříznutí zadané znaky.  
  
## <a name="the-changes"></a>Změny  
 Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, cesta normalizace došlo ke změně následujícími způsoby:  
  
- Modul runtime odloží do operačního systému [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkce normalizace cesty.  
  
- Normalizace už zahrnuje ořezávání konec segmenty adresáře (například mezeru na konci názvu adresáře).  
  
- Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně `\\.\` a pro rozhraní API vstupně-výstupní operace souboru v mscorlib.dll, `\\?\`.  
  
- Modul runtime nelze ověřit zařízení syntaxe cesty.  
  
- Použití syntaxe zařízení pro přístup k alternativní datové proudy je podporované.  
  
## <a name="impact"></a>Dopad  

Pro aplikace, které cílí .NET Framework 4.6.2 nebo novější, tyto změny jsou standardně povoleny. By měl pomáhají zvýšit výkon při povolení metody pro přístup k dříve nedostupných cesty.  
  
Aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší verze, ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novější se tato změna nemá vliv.  
  
## <a name="mitigation"></a>Zmírnění  
 Aplikace, které cílí .NET Framework 4.6.2 nebo novější můžete zrušit to změnit a použít starší verzi normalizace přidáním následujícího [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
Aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo starší ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novější můžete povolit změny normalizace cestu tak, že přidáte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část soubor .configuration aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
