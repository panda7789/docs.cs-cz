---
title: 'Omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName'
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
ms.openlocfilehash: eba871215f33e4d3b50054e9ceaa92be090d0143
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871108"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName
Počínaje aplikací, které se zaměřují [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], cesta oddělovač použitý v <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnost se změnil z zpětné lomítko ("\\") používají v předchozích verzích rozhraní .NET Framework na dopředné lomítko ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objekty byly vytvořeny zavoláním jednoho z přetížení <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Dopad  
 Tato změna přináší implementace .NET do souladu s část 4.4.17.1 [. Specifikaci formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Na systémech než Windows dekomprimovat archivy ZIP.  
  
 Dekomprese souboru zip vytvořil aplikaci, který cílí předchozí verze rozhraní .NET Framework v operačních systémech než Windows například Macintosh selže zachovat adresářovou strukturu. Například na Macintosh, vytvoří sadu souborů, jejichž název souboru zřetězí cesta k adresáři, spolu s jakékoli zpětné lomítko ("\\") znaků a název souboru. V důsledku toho se nezachová struktura adresářů dekomprimovaných souborů.  
  
 Dopad na tuto změnu. Soubory ZIP, které jsou v operačním systému Windows dekomprimovat rozhraní API v rozhraní .NET Framework <xref:System.IO> oborem názvů musí být minimální, protože tato rozhraní API bez problémů zvládne lomítko ("/") nebo zpětné lomítko ("\\") jako oddělovač cesty.  
  
## <a name="mitigation"></a>Zmírnění  
 Pokud toto chování nežádoucí, můžete se rozhodnout z přidáním nastavení konfigurace, které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad zobrazuje i `<runtime>` části a výslovného nesouhlasu s přepínačem.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny na [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování tak, že přidáte nastavení konfigurace, které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurační soubor aplikace. Následující příklad zobrazuje i `<runtime>` části a přepínač opt-in.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [Kompatibilita aplikací ve verzi 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
