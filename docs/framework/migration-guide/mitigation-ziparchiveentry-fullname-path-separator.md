---
title: Zmírnění ZipArchiveEntry. FullName – oddělovač cest
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b97436ca2f81fea139689c7c2c2348718827b90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778859"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Zmírnění ZipArchiveEntry. FullName – oddělovač cest
Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, se oddělovač cest použitý ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnosti změnil z zpětného lomítka\\("") používaného v předchozích verzích .NET Framework na lomítko ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořeny voláním jednoho z přetížení <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Dopad  
 Tato změna přináší implementaci rozhraní .NET do souladu s oddílem 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Archivy ZIP, které se mají dekomprimovat v systémech jiných než Windows  
  
 Dekomprimace souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi .NET Framework v operačních systémech jiných než Windows, jako je například Macintosh, se nepodařilo zachovat adresářovou strukturu. Například v počítači Macintosh vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři, spolu se znakem zpětného lomítka ("\\") a názvem souboru. V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.  
  
 Dopad této změny na. Soubory zip, které jsou v operačním systému Windows dekomprimovány pomocí rozhraní API v <xref:System.IO> oboru názvů .NET Framework, by měly mít minimální hodnotu, protože tato rozhraní API můžou bez problémů zpracovávat lomítka ("/") nebo\\zpětné lomítko ("") jako znak oddělovače cesty.  
  
## <a name="mitigation"></a>Zmírnění  
 Pokud je toto chování nežádoucí, můžete se odhlásit přidáním nastavení konfigurace do [ \<oddílu modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace. Následující příklad ukazuje `<runtime>` oddíl i přepínač pro odhlášení.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží na .NET Framework 4.6.1 a novějších verzích, se můžou k tomuto chování vyjádřit přidáním nastavení konfigurace do [ \<části modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) aplikace. konfigurační soubor. Následující příklad ukazuje `<runtime>` oddíl i přepínač pro výslovný souhlas.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6-1.md)
- [Kompatibilita aplikací v 4.6.1](application-compatibility-in-the-net-framework-4-6-1.md)
