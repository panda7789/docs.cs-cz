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
ms.openlocfilehash: 3940cf8d1ebda668925a5c461b84a8bc61550476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName
Počínaje aplikací cílených [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], cesta oddělovač použitý v <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnost bylo změněno z zpětné lomítko ("\\") používají v předchozích verzích rozhraní .NET Framework na dopředné lomítko ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objekty jsou vytvořené pomocí jednoho z přetížení volání <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metoda.  
  
## <a name="impact"></a>Dopad  
 Tato změna přináší implementace rozhraní .NET do souladu s části 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. ZIP archivy k dekomprimaci na jiné operační systémy.  
  
 Dekompresi soubor zip vytvořené aplikace s cílem předchozí verzi rozhraní .NET Framework na jiný systém než Windows operační systémy, třeba Macintosh nepodaří zachovat strukturu adresáře. Například na Macintosh, vytvoří sadu souborů, jejichž název souboru zřetězí cesta k adresáři, společně s žádné zpětné lomítko ("\\") znaků a název souboru. V důsledku toho není zachován struktura adresářů dekomprimovaných souborů.  
  
 Dopad na tuto změnu. Soubory ZIP, které jsou dekomprimovat operačního systému Windows pomocí rozhraní API v rozhraní .NET Framework <xref:System.IO> oboru názvů musí být minimální, protože tato rozhraní API může bezproblémově zpracovat lomítko ("/") ani zpětné lomítko ("\\") jako cesta oddělovací znak.  
  
## <a name="mitigation"></a>Zmírnění  
 Pokud je toto chování žádoucí, můžete zvolit z přidáním nastavení konfigurace, pro které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddíl konfiguračního souboru aplikace. Následující příklad zobrazuje i `<runtime>` části a vyjádření výslovného nesouhlasu s přepínačem.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozích verzích rozhraní .NET Framework, ale jsou spuštěny na [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování přidáním nastavení konfigurace, pro které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurační soubor aplikace. Následující příklad zobrazuje i `<runtime>` části a přepínače přihlášení.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 [Kompatibilita aplikací v 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
