---
title: Stínové kopírování sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572291fa5674c541136e587bc40818da85f71a65
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192730"
---
# <a name="shadow-copying-assemblies"></a>Stínové kopírování sestavení
Stínové kopírování sestavení umožňuje, které se používají v doméně aplikace aktualizovat bez uvolnění domény aplikace. To je užitečné hlavně pro aplikace, které musí být k dispozici nepřetržitě, jako jsou weby ASP.NET.  
  
> [!IMPORTANT]
>  Stínové kopírování sestavení se nepodporuje v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 Modul common language runtime uzamkne soubor sestavení, když je sestavení načteno, proto ho nejde aktualizovat, dokud sestavení není uvolněn. Jediný způsob, jak odinstalovat sestavení z domény aplikace je uvolnění domény aplikace, takže za normálních okolností sestavení nelze do všech doménách aplikace, které používají aktualizovat na disku mají byl uvolněn.  
  
 Pokud domény aplikace je nakonfigurovaná pro stínové kopie souborů, jsou sestavení z cesty aplikace zkopírován do jiného umístění a načíst z tohoto umístění. Kopie zašifrovaná, ale původní soubor sestavení je odemknutá a je možné aktualizovat.  
  
> [!IMPORTANT]
>  Pouze sestavení, které mohou být stínové kopie jsou ty uložené v adresáři aplikace nebo jeho podadresářů, které jsou určené <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnosti, pokud je nakonfigurované domény aplikace. Sestavení, které jsou uloženy v globální mezipaměti sestavení nejsou stínové kopie.  
  
 Tento článek obsahuje následující části:  
  
-   [Povolení a používání stínové kopírování sestavení](#EnablingAndUsing) popisuje základní použití a možnosti, které jsou k dispozici pro stínové kopírování sestavení.  
  
-   [Výkon při spouštění](#StartupPerformance) jsou zde popsány změny, které jsou provedeny stínovém kopírování v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] zlepšit výkon při spouštění a jak se vrátit k chování z předchozích verzí.  
  
-   [Zastaralé metody](#ObsoleteMethods) jsou zde popsány změny, které byly provedeny k vlastnostem a metodám, které řídí stínové kopírování v [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)].  
  
<a name="EnablingAndUsing"></a>   
## <a name="enabling-and-using-shadow-copying"></a>Povolení a používání stínové kopírování sestavení  
 Můžete použít vlastnosti <xref:System.AppDomainSetup> třídy následujícím způsobem, aby konfigurace domény aplikace pro stínové kopírování sestavení:  
  
-   Povolit stínové kopírování tak, že nastavíte <xref:System.AppDomainSetup.ShadowCopyFiles%2A> vlastnost na hodnotu řetězce `"true"`.  
  
     Ve výchozím nastavení toto nastavení způsobí, že všechna sestavení v cesta aplikace, které se mají zkopírovat do mezipaměti pro stahování před načtením. Jedná se o stejné mezipaměti udržuje modul common language runtime k ukládání souborů stažených z jiných počítačů, a modul common language runtime automaticky odstraní soubory, pokud už nepotřebujete.  
  
-   Volitelně můžete nastavit pomocí vlastní umístění pro soubory stínové kopie <xref:System.AppDomainSetup.CachePath%2A> vlastnost a <xref:System.AppDomainSetup.ApplicationName%2A> vlastnost.  
  
     Základní cesta pro umístění je vytvořený zřetězením <xref:System.AppDomainSetup.ApplicationName%2A> vlastnost <xref:System.AppDomainSetup.CachePath%2A> jako podadresáře. Sestavení jsou stínové zkopírovány do podsložek této cesty, ne pro samotné základní cesty.  
  
    > [!NOTE]
    >  Pokud <xref:System.AppDomainSetup.ApplicationName%2A> vlastnost není nastavená, <xref:System.AppDomainSetup.CachePath%2A> vlastnost se ignoruje, a je použita mezipaměť pro stahování. Není vyvolána žádná výjimka.  
  
     Pokud chcete zadat vlastní umístění, zodpovídají za čištění adresáře a soubory zkopírovány, pokud už nepotřebujete. Se neodstraní automaticky.  
  
     Existuje několik důvodů, proč můžete chtít nastavit vlastní umístění pro soubory stínové kopie. Můžete nastavit vlastní umístění pro soubory stínové kopie, pokud vaše aplikace generuje mnoho kopií. Mezipaměť pro stahování má omezenou velikost, nikoli podle doby života, takže je možné, že se pokusí odstranit soubor, který je stále používán common language runtime. Dalším důvodem pro nastavení vlastního umístění je, pokud uživatelé používají vaše aplikace nemá oprávnění k zápisu do adresáře, který používá modul common language runtime pro mezipaměť pro stahování.  
  
-   Volitelně omezte sestavení, které jsou stínové kopie pomocí <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> vlastnost.  
  
     Když povolíte stínové kopírování sestavení aplikační domény, výchozí hodnota je zkopírovat všechna sestavení v cestě aplikace – to znamená, že v adresářích určené <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnosti. Můžete omezit kopírování do vybraného adresáře vytváření řetězec, který obsahuje jenom adresáře, které chcete stínové kopie a přiřazování řetězec, který má <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> vlastnost. Adresáře oddělte středníkem. Pouze sestavení, které jsou stínové kopie jsou ty, které ve vybraných složkách.  
  
    > [!NOTE]
    >  Pokud nepřiřadíte řetězec <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> vlastnost, nebo pokud nastavíte tuto vlastnost na `null`, všechna sestavení v adresářích určených <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnosti jsou stínové kopie.  
  
    > [!IMPORTANT]
    >  Cesty k adresářům nesmí obsahovat středníky, protože je znak oddělovač středník. Neexistuje žádný řídicí znak pro středníky.  
  
<a name="StartupPerformance"></a>   
## <a name="startup-performance"></a>Výkon při spuštění  
 Při spuštění aplikační doménu, která používá stínové kopírování sestavení, dochází ke zpoždění při sestavení v adresáři aplikace jsou zkopírovány do adresáře stínové kopie nebo ověřit, zda jsou již v tomto umístění. Před [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], všechna sestavení, které byly zkopírovány do dočasného adresáře. Každé sestavení byl otevřen kvůli ověření názvu sestavení a byl ověřen silný název. Pokud chcete zobrazit, zda bylo aktualizováno později, než kopírování v adresáři stínové kopie došlo k zaškrtnutí každé sestavení. Pokud ano, byl zkopírován do adresáře stínové kopie. A konečně byly zrušeny dočasné kopie.  
  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], můžete přímo porovnat soubor datum a čas každého sestavení v adresáři aplikace pomocí souboru datum a čas kopie v adresáři stínové kopie je výchozí chování při spuštění. Pokud sestavení se aktualizovala, je zkopírován pomocí stejného postupu jako v předchozích verzích rozhraní .NET Framework. v opačném případě je načtena kopie v adresáři stínové kopie.  
  
 Výsledný zlepšení výkonu je největší pro aplikace, ve kterých sestavení se nemění často, a obvykle změn v malou podmnožinu sestavení. Pokud většinou sestavení v aplikace často mění, nový výchozí chování může způsobit snížení výkonu. Chování při spuštění z předchozích verzí rozhraní .NET Framework můžete obnovit tak, že přidáte [ \<shadowCopyVerifyByTimestamp > element](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) do konfiguračního souboru, s `enabled="false"`.  
  
<a name="ObsoleteMethods"></a>   
## <a name="obsolete-methods"></a>Zastaralé metody  
 <xref:System.AppDomain> Třída má několik metod, jako například <xref:System.AppDomain.SetShadowCopyFiles%2A> a <xref:System.AppDomain.ClearShadowCopyPath%2A>, který lze použít k řízení stínové kopírování sestavení na doménu aplikace, ale ty jsou označené za zastaralé v rozhraní .NET Framework verze 2.0. Doporučeným způsobem, jak nakonfigurovat doménu aplikace pro stínové kopírování sestavení, je použít vlastnosti <xref:System.AppDomainSetup> třídy.  
  
## <a name="see-also"></a>Viz také  
- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>  
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>  
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>  
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>  
- [\<shadowCopyVerifyByTimestamp > – Element](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
