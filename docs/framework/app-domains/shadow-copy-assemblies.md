---
title: Stínové kopírování sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
ms.openlocfilehash: 40a1b5062d45b7b540af7058b82b77c664070d2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119782"
---
# <a name="shadow-copying-assemblies"></a>Stínové kopírování sestavení

Stínové kopírování umožňuje aktualizovat sestavení, která se používají v doméně aplikace, bez uvolnění domény aplikace. To je zvlášť užitečné pro aplikace, které musí být k dispozici průběžně, například ASP.NET lokality.

> [!IMPORTANT]
> Stínové kopírování se v aplikacích [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] nepodporuje.

Modul CLR (Common Language Runtime) zamkne soubor sestavení, když je sestavení načteno, takže soubor nelze aktualizovat, dokud nebude sestavení uvolněno. Jediným způsobem, jak uvolnit sestavení z domény aplikace, je uvolnění domény aplikace, takže za normálních okolností nemůže být sestavení na disku aktualizováno, dokud nebudou všechny domény aplikace, které ji používají, uvolněny.

Když je doména aplikace nakonfigurovaná na soubory stínové kopie, sestavení z cesty aplikace se zkopírují do jiného umístění a načtou z tohoto umístění. Kopie je uzamčena, ale původní soubor sestavení je odemčen a lze jej aktualizovat.

> [!IMPORTANT]
> Pouze sestavení, která lze kopírovat pomocí stínové kopie, jsou uložena v adresáři aplikace nebo v jeho podadresářích, které jsou určeny <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastností při konfiguraci domény aplikace. Sestavení uložená v globální mezipaměti sestavení (GAC) nejsou zkopírována stínem.

Tento článek obsahuje následující oddíly:

- [Povolení a použití stínového kopírování](#EnablingAndUsing) popisuje základní použití a možnosti, které jsou k dispozici pro stínové kopírování.

- [Výkon při spuštění](#StartupPerformance) popisuje změny stínového kopírování v .NET Framework 4 pro zlepšení výkonu při spuštění a postup obnovení na chování starších verzí.

- [Zastaralé metody](#ObsoleteMethods) popisují změny vlastností a metod, které řídí stínové kopírování v .NET Framework 2,0.

<a name="EnablingAndUsing"></a>

## <a name="enabling-and-using-shadow-copying"></a>Povolení a použití stínového kopírování

Můžete použít vlastnosti třídy <xref:System.AppDomainSetup> následujícím způsobem pro konfiguraci domény aplikace pro stínové kopírování:

- Povolte stínové kopírování nastavením vlastnosti <xref:System.AppDomainSetup.ShadowCopyFiles%2A> na hodnotu řetězce `"true"`.

  Ve výchozím nastavení toto nastavení způsobí, že všechna sestavení v cestě aplikace budou zkopírována do mezipaměti pro stahování před jejich načtením. Toto je stejná mezipaměť, kterou udržuje modul CLR (Common Language Runtime) pro ukládání souborů stažených z jiných počítačů, a modul CLR (Common Language Runtime) soubory automaticky odstraní, když už nejsou potřeba.

- Volitelně můžete nastavit vlastní umístění pro stínové zkopírované soubory pomocí vlastnosti <xref:System.AppDomainSetup.CachePath%2A> a vlastnosti <xref:System.AppDomainSetup.ApplicationName%2A>.

  Základní cesta pro umístění je vytvořena zřetězením vlastnosti <xref:System.AppDomainSetup.ApplicationName%2A> k vlastnosti <xref:System.AppDomainSetup.CachePath%2A> jako podadresáři. Sestavení jsou stínové zkopírovány do podadresářů této cesty, nikoli do samotné základní cesty.

  > [!NOTE]
  > Pokud vlastnost <xref:System.AppDomainSetup.ApplicationName%2A> není nastavena, je vlastnost <xref:System.AppDomainSetup.CachePath%2A> ignorována a je použita mezipaměť pro stahování. Není vyvolána žádná výjimka.

  Pokud zadáte vlastní umístění, zodpovídáte za vyčištění adresářů a kopírovaných souborů, pokud už je nepotřebujete. Neodstraňují se automaticky.

  Existuje několik důvodů, proč možná budete chtít nastavit vlastní umístění pro stínové zkopírované soubory. Pokud vaše aplikace generuje velký počet kopií, je vhodné nastavit vlastní umístění pro stínové zkopírované soubory. Mezipaměť pro stahování je omezená velikostí, ne po dobu života, takže je možné, že se modul CLR (Common Language Runtime) pokusí odstranit soubor, který se pořád používá. Dalším důvodem pro nastavení vlastního umístění je, že uživatelé, kteří spouštějí vaši aplikaci, nemají přístup pro zápis do umístění adresáře, které modul CLR (Common Language Runtime) používá pro mezipaměť pro stahování.

- Volitelně můžete omezit sestavení, která jsou Stínová kopie, pomocí vlastnosti <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>.

  Pokud povolíte stínové kopírování pro doménu aplikace, ve výchozím nastavení je zkopírování všech sestavení v cestě aplikace, tj. v adresářích určených <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A>ch vlastností. Kopírování můžete omezit na vybrané adresáře vytvořením řetězce, který obsahuje pouze ty adresáře, které chcete stínovou kopii, a přiřazením řetězce k vlastnosti <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>. Adresáře oddělte středníkem. Pouze sestavení, která jsou stínové kopie, jsou ta ve vybraných adresářích.

  > [!NOTE]
  > Pokud nepřiřazujete řetězec vlastnosti <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, nebo pokud nastavíte tuto vlastnost na `null`, všechna sestavení v adresářích určených <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A>ch vlastností jsou stínové kopie.

  > [!IMPORTANT]
  > Cesty k adresáři nesmí obsahovat středník, protože středník je znak oddělovače. Neexistují žádné řídicí znaky pro středníky.

<a name="StartupPerformance"></a>

## <a name="startup-performance"></a>Výkon při spuštění

Když se spustí doména aplikace, která používá stínové kopírování, dojde ke zpoždění během kopírování sestavení v adresáři aplikace do adresáře stínové kopie nebo při ověření, jestli už jsou v tomto umístění. Před .NET Framework 4 byla všechna sestavení zkopírována do dočasného adresáře. Každé sestavení bylo otevřeno pro ověření názvu sestavení a silného názvu bylo ověřeno. Každé sestavení bylo zkontrolováno, zda bylo aktualizováno později než kopírování v adresáři stínové kopie. V takovém případě se zkopíroval do adresáře stínové kopie. Nakonec byly dočasné kopie zahozeny.

Počínaje .NET Framework 4 je výchozí chování při spuštění přímo porovnat datum a čas každého sestavení v adresáři aplikace s datem a časem kopírování v adresáři stínové kopie. Pokud bylo sestavení aktualizováno, je zkopírováno pomocí stejného postupu jako v předchozích verzích .NET Framework; v opačném případě je kopie v adresáři stínové kopie načtena.

Výsledné zlepšení výkonu je největší pro aplikace, ve kterých se sestavení často nemění a změny se většinou vyskytují v malých podmnožině sestavení. Pokud se většina sestavení v aplikaci často mění, může nové výchozí chování způsobit regresi výkonu. Můžete obnovit chování při spuštění předchozích verzí .NET Framework přidáním [prvku\<shadowCopyVerifyByTimestamp >](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) do konfiguračního souboru s `enabled="false"`.

<a name="ObsoleteMethods"></a>

## <a name="obsolete-methods"></a>Zastaralé metody

Třída <xref:System.AppDomain> obsahuje několik metod, například <xref:System.AppDomain.SetShadowCopyFiles%2A> a <xref:System.AppDomain.ClearShadowCopyPath%2A>, které lze použít k řízení stínového kopírování v doméně aplikace, ale ty jsou v .NET Framework verze 2,0 označeny jako zastaralé. Doporučeným způsobem konfigurace aplikační domény pro stínové kopírování je použití vlastností třídy <xref:System.AppDomainSetup>.

## <a name="see-also"></a>Viz také:

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [\<element > shadowCopyVerifyByTimestamp](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
