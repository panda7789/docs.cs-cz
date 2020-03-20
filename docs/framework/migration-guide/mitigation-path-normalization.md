---
title: 'Zmírnění: Normalizace cesty'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181236"
---
# <a name="mitigation-path-normalization"></a>Zmírnění: Normalizace cesty
Počínaje aplikacemi cíl .NET Framework 4.6.2, cesta normalizace v rozhraní .NET Framework se změnil.  
  
## <a name="what-is-path-normalization"></a>Co je normalizace cesty?  
 Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby odpovídalplatné cestě v cílovém operačním systému. Normalizace obvykle zahrnuje:  
  
- Oddělovače komponent a adresářů canonicalizing.  
  
- Použití aktuálního adresáře na relativní cestu.  
  
- Vyhodnocení relativního adresáře (`.`)`..`nebo nadřazeného adresáře ( ) v cestě.  
  
- Oříznutí určených znaků.  
  
## <a name="the-changes"></a>Změny  
 Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, se normalizace cesty změnila následujícími způsoby:  
  
- Runtime odkládá na funkci [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) operačního systému normalizovat cesty.  
  
- Normalizace již nezahrnuje oříznutí konce segmentů adresáře (například mezeru na konci názvu adresáře).  
  
- Podpora syntaxe cesty zařízení v `\\.\` plném vztahu důvěryhodnosti, včetně rozhraní API vstupně-nosných souborů v souboru mscorlib.dll . `\\?\`  
  
- Runtime neověřuje cesty syntaxe zařízení.  
  
- Je podporováno použití syntaxe zařízení pro přístup k alternativním datovým proudům.  
  
## <a name="impact"></a>Dopad  

U aplikací, které cílí na rozhraní .NET Framework 4.6.2 nebo novější, jsou tyto změny ve výchozím nastavení zapnuté. Měly by zlepšit výkon a zároveň umožnit metodám přístup k dříve nepřístupným cestám.  
  
Aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší verze, ale jsou spuštěny v rámci rozhraní .NET Framework 4.6.2 nebo novější, nejsou touto změnou ovlivněny.  
  
## <a name="mitigation"></a>Omezení rizik  
 Aplikace, které cílí na rozhraní .NET Framework 4.6.2 nebo novější, se mohou odhlásit z této změny a používat starší normalizaci přidáním následujících položek do části konfigurace aplikace [ \<>runtime:](../configure-apps/file-schema/runtime/runtime-element.md)  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
Aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo starší, ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novějším, mohou povolit změny normalizace cesty přidáním následujícího řádku do části [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru konfigurace aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
