---
title: 'Zmírnění: normalizace cest'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 1e7b540975b84320d099ca004df5b6a87aa60f6a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457882"
---
# <a name="mitigation-path-normalization"></a>Zmírnění: normalizace cest
Počínaje aplikacemi cílíte na .NET Framework 4.6.2, normalizace cest v .NET Framework se změnila.  
  
## <a name="what-is-path-normalization"></a>Co je normalizace cest?  
 Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby splňoval platnou cestu v cílovém operačním systému. Normalizace obvykle zahrnuje:  
  
- Kanonizace součásti a oddělovače adresářů.  
  
- Použití aktuálního adresáře na relativní cestu.  
  
- Vyhodnocení relativního adresáře (`.`) nebo nadřazeného adresáře (`..`) v cestě.  
  
- Ořezávání zadaných znaků.  
  
## <a name="the-changes"></a>Změny  
 Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, se normalizace cesty změnila následujícími způsoby:  
  
- Modul runtime se odkládá na funkci [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) operačního systému k normalizaci cest.  
  
- Normalizace už nezahrnuje oříznutí konce segmentů adresáře (například místa na konci názvu adresáře).  
  
- Podpora syntaxe cesty zařízení v úplném vztahu důvěryhodnosti, včetně `\\.\` a, pro vstupně-výstupní rozhraní API souborů v knihovně Mscorlib. dll `\\?\`.  
  
- Modul runtime neověřuje cestu k syntaxi zařízení.  
  
- Podporuje se použití syntaxe zařízení pro přístup k alternativním datovým proudům.  
  
## <a name="impact"></a>Dopad  

U aplikací, které cílí na .NET Framework 4.6.2 nebo novějším, jsou tyto změny ve výchozím nastavení zapnuté. Měli byste zvýšit výkon a zároveň povolit přístup k dříve nepřístupným cestám k těmto metodám.  
  
Aplikace, které cílí na .NET Framework 4.6.1 a starší verze, ale jsou spuštěné v .NET Framework 4.6.2 nebo novějším, tato změna neovlivní.  
  
## <a name="mitigation"></a>Zmírnění  
 Aplikace, které cílí na .NET Framework 4.6.2 nebo novější, si mohou tuto změnu odhlásit a použít starší normalizaci přidáním následujícího do části [\<modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
Aplikace, které cílí na .NET Framework 4.6.1 nebo starší, ale běží na .NET Framework 4.6.2 nebo novějším, můžou povolit normalizaci cest přidáním následujícího řádku do části [> modulu runtime\<](../configure-apps/file-schema/runtime/runtime-element.md) souboru Application. Configuration:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
