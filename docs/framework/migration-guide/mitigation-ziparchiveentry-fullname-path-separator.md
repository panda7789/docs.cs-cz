---
title: 'Zmírnění rizika: ZipArchiveEntry. FullName – oddělovač cest'
description: Přečtěte si, jak se oddělovač cest pro vlastnost ZipArchiveEntry. FullName změnil počínaje aplikacemi, které cílí na .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475291"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Zmírnění rizika: ZipArchiveEntry. FullName – oddělovač cest

Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, se oddělovač cest použitý ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnosti změnil z zpětného lomítka (" \\ ") používaného v předchozích verzích .NET Framework na lomítko ("/"). <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořeny voláním jednoho z přetížení <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Dopad  
 Tato změna přináší implementaci rozhraní .NET do souladu s oddílem 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Archivy ZIP, které se mají dekomprimovat v systémech jiných než Windows  
  
 Dekomprimace souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi .NET Framework v operačních systémech jiných než Windows, jako je například MacOS, se nepodařilo zachovat adresářovou strukturu. Například v MacOS vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři, znak zpětného lomítka (" \\ ") a název souboru. V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.  
  
 Dopad této změny na. Soubory ZIP, které jsou v operačním systému Windows dekomprimovány pomocí rozhraní API v .NET Framework <xref:System.IO> obor názvů by měly být minimální, protože tato rozhraní API můžou hladě zpracovávat lomítko ("/") nebo zpětné lomítko (" \\ ") jako znak oddělovače cesty.  
  
## <a name="mitigation"></a>Omezení rizik  
 Pokud je toto chování nežádoucí, můžete se odhlásit přidáním nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad ukazuje `<runtime>` oddíl i přepínač pro odhlášení.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad ukazuje `<runtime>` oddíl i přepínač pro výslovný souhlas.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
