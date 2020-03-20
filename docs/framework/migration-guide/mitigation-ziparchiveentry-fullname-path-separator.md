---
title: 'Zmírnění: Oddělovač cesty ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 021d22e90ba39a4d01cf7d64588fab2d724b6640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457732"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Zmírnění: Oddělovač cesty ZipArchiveEntry.FullName
Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.1, oddělovač cesty použitý ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnosti se změnil z zpětného lomítka ("\\") používaného v předchozích verzích rozhraní .NET Framework na lomítko ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořeny voláním jednoho <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> z přetížení metody.  
  
## <a name="impact"></a>Dopad  
 Změna uvede implementaci .NET do souladu s oddílem 4.4.17.1 [. SPECIFIKACE FORMÁTU SOUBORU ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje . ZIP archivy, které mají být dekomprimovány v systémech, které nejsou systémy Windows.  
  
 Dekomprese souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi rozhraní .NET Framework v operačních systémech, například v systému Macintosh, nezachová adresářovou strukturu. Například na Macintosh vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři,\\spolu s případnými znaky zpětného lomítka (" a názvem souboru. V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.  
  
 Dopad této změny na . Soubory ZIP, které jsou dekomprimovány v operačním systému <xref:System.IO> Windows pomocí rozhraní API v oboru názvů rozhraní .NET Framework, by měly\\být minimální, protože tato rozhraní API mohou bez problémů zpracovat lomítko ("/") nebo zpětné lomítko (" ") jako znak oddělovače cesty.  
  
## <a name="mitigation"></a>Omezení rizik  
 Pokud je toto chování nežádoucí, můžete se odhlásit přidáním nastavení konfigurace do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace. V následujícím textu `<runtime>` je uveden oddíl i přepínač pro odhlášení.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6.1 a novějšíverze můžete přihlásit k tomuto chování přidáním nastavení konfigurace [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části konfiguračního souboru aplikace. V následujícím textu `<runtime>` je uveden oddíl i přepínač pro přihlášení.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Viz také

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6-1.md)
- [Kompatibilita aplikací](application-compatibility.md)
