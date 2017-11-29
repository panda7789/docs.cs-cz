---
title: "Stínové kopírování sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2eb71e1d03da16581ee25bf972be51ee2f63f585
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="shadow-copying-assemblies"></a>Stínové kopírování sestavení
Stínové kopírování sestavení povoluje, které se používají v doméně aplikace aktualizovat bez uvolnění domény aplikace. To je zvlášť užitečné pro aplikace, které musí být k dispozici nepřetržitě, jako je například weby technologie ASP.NET.  
  
> [!IMPORTANT]
>  Stínové kopírování sestavení není podporována v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 Modul common language runtime uzamkne soubor sestavení, když je sestavení načíst, takže soubor nelze aktualizovat, dokud sestavení je odpojen. Jediný způsob, jak uvolnit sestavení z domény aplikace je uvolnění domény aplikace, takže za normálních podmínek sestavení nelze aktualizovat, na disku dokud všechny domény aplikace, které používají ho byly odstraněny.  
  
 Pokud domény aplikace je nakonfigurovaná pro stínové kopie souborů, sestavení z cesta k aplikaci zkopírovány do jiného umístění a načíst z tohoto umístění. Kopie uzamčeno, ale původní soubor sestavení je odemčený a může být aktualizován.  
  
> [!IMPORTANT]
>  Pouze sestavení, které mohou být stínové kopie jsou ty, uložené v adresáři aplikace nebo jeho podadresářů, určeného <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnosti při konfiguraci domény aplikace. Sestavení, které jsou uložené v globální mezipaměti sestavení nejsou stínové kopie.  
  
 Tento článek obsahuje následující části:  
  
-   [Povolení a používání stínové kopírování sestavení](#EnablingAndUsing) popisuje základní použití a možnosti, které jsou k dispozici pro stínové kopírování sestavení.  
  
-   [Výkon při spouštění](#StartupPerformance) popisuje změny, které jsou vytvářeny stínovém kopírování v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ke zlepšení výkonu spuštění a jak se vrátit k chování starší verze.  
  
-   [Zastaralé metody](#ObsoleteMethods) popisuje změny, které byly provedeny vlastnosti a metody, které řídí stínové kopírování v [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)].  
  
<a name="EnablingAndUsing"></a>   
## <a name="enabling-and-using-shadow-copying"></a>Povolení a používání stínové kopírování sestavení  
 Můžete použít vlastnosti <xref:System.AppDomainSetup> třídy následujícím způsobem, aby konfigurace domény aplikace pro stínové kopírování sestavení:  
  
-   Povolte stínové kopírování nastavením <xref:System.AppDomainSetup.ShadowCopyFiles%2A> vlastnost na hodnotu řetězce `"true"`.  
  
     Ve výchozím nastavení toto nastavení způsobí, že všechna sestavení v cestě aplikace před načtením zkopírovány do mezipaměti pro stahování. Toto je stejný mezipaměti udržované modul common language runtime ukládat soubory stahované z jiných počítačů a modul common language runtime automaticky odstraní soubory, když už nejsou potřeba.  
  
-   Volitelně můžete nastavit vlastní umístění souborů služby stínové kopie vytvořené pomocí <xref:System.AppDomainSetup.CachePath%2A> vlastnost a <xref:System.AppDomainSetup.ApplicationName%2A> vlastnost.  
  
     Základní cesta pro umístění je tvořena zřetězením <xref:System.AppDomainSetup.ApplicationName%2A> vlastnost, která má <xref:System.AppDomainSetup.CachePath%2A> jako podadresáře. Sestavení jsou zkopírována do podadresáře této cesty, ne pro samotné základní cesty.  
  
    > [!NOTE]
    >  Pokud <xref:System.AppDomainSetup.ApplicationName%2A> není vlastnost nastavena, <xref:System.AppDomainSetup.CachePath%2A> vlastnost je ignorována a je použita mezipaměť pro stahování. Nedojde k výjimce.  
  
     Pokud zadáte do vlastního umístění, jsou zodpovědní za vyčištění adresářů a zkopírovat soubory, když už nejsou potřeba. Nejsou automaticky odstraněny.  
  
     Existuje několik důvodů, proč můžete chtít nastavit vlastní umístění pro soubory stínové kopie. Můžete chtít nastavit vlastní umístění pro soubory stínové kopie, pokud vaše aplikace generuje velký počet kopií. Mezipaměť pro stahování je omezená, velikost, nikoli životnost, takže je možné, že bude modul common language runtime pokusu o odstranění souboru, který je stále používáno. Dalším důvodem pro nastavení vlastního umístění je při spuštění aplikace uživatelé nebudou mít přístup pro zápis k umístění adresáře, který používá modul common language runtime pro mezipaměť pro stahování.  
  
-   Volitelně můžete omezit sestavení, které jsou stínové kopie pomocí <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> vlastnost.  
  
     Když povolíte stínové kopírování sestavení pro doménu aplikace, ve výchozím nastavení se zkopírovat všechna sestavení v cesta k aplikaci – to znamená adresáře určené pomocí <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnosti. Můžete omezit kopírování na vybrané adresáře vytvořením řetězec, který obsahuje pouze adresáře, které chcete stínové kopie a přiřadit řetězec, který má <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> vlastnost. Adresáře oddělte středníky. Pouze sestavení, které jsou stínové kopie jsou zadány ve vybraných složkách.  
  
    > [!NOTE]
    >  Pokud nepřiřadíte řetězec tak, aby <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> vlastnost, nebo pokud tuto vlastnost nastavíte na `null`, všechna sestavení v adresáři určeného <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnosti jsou stínové kopie.  
  
    > [!IMPORTANT]
    >  Cesty k adresáři nesmí obsahovat středníky, protože je středník oddělovací znak. Neexistuje žádný řídicí znak pro středníky.  
  
<a name="StartupPerformance"></a>   
## <a name="startup-performance"></a>Výkon při spouštění  
 Když se spustí doménu aplikace, která používá stínové kopírování sestavení, dochází ke zpoždění při sestavení v adresáři aplikace jsou zkopírovány do adresáře stínové kopie nebo ověřit, zda jsou již v tomto umístění. Před [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], všechny sestavení, které byly zkopírovány do dočasného adresáře. Každé sestavení bylo otevřeno pro ověření název sestavení a byl ověřen silný název. Každé sestavení zkontroloval se zda bylo aktualizováno později, než kopie v adresáři stínové kopie. Pokud ano, byl zkopírován do adresáře stínové kopie. Nakonec dočasná kopie byly zrušeny.  
  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], výchozí chování při spuštění je přímo porovnat soubor datum a čas každé sestavení v adresáři aplikace s souboru datum a čas kopie v adresáři stínové kopie. Pokud sestavení byl aktualizován, se zkopíruje pomocí stejného postupu jako v předchozích verzích rozhraní .NET Framework; jinak je načten kopie v adresáři stínové kopie.  
  
 Výsledné zlepšení výkonu je největší pro aplikace, ve kterých sestavení často nemění a změny jsou obvykle prováděny v malou podmnožinu sestavení. Pokud se většina sestavení v o změnu aplikace často, nové výchozí chování může způsobit snížení výkonu. Chování při spuštění z předchozí verze rozhraní .NET Framework můžete obnovit tak, že přidáte [ \<shadowCopyVerifyByTimestamp > element](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) do konfiguračního souboru s `enabled="false"`.  
  
<a name="ObsoleteMethods"></a>   
## <a name="obsolete-methods"></a>Zastaralé metody  
 <xref:System.AppDomain> Třída obsahuje několik metod, jako například <xref:System.AppDomain.SetShadowCopyFiles%2A> a <xref:System.AppDomain.ClearShadowCopyPath%2A>, který lze použít k řízení stínové kopírování na doménu aplikace, ale tyto byly označeny jako zastaralé v rozhraní .NET Framework verze 2.0. Doporučený způsob konfigurace domény aplikace pro stínové kopírování sestavení je použití vlastnosti <xref:System.AppDomainSetup> třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>  
 [\<shadowCopyVerifyByTimestamp > elementu](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
