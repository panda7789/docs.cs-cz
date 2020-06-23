---
title: Stínové kopírování sestavení
description: Prozkoumejte stínové kopírování sestavení v rozhraní .NET, takže ty, které se používají v doméně aplikace, lze aktualizovat bez uvolnění domény aplikace.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
ms.openlocfilehash: a7ff72763dd26dbc50cd37e070c2d25ababa00f3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104562"
---
# <a name="shadow-copying-assemblies"></a>Stínové kopírování sestavení

Stínové kopírování umožňuje aktualizovat sestavení, která se používají v doméně aplikace, bez uvolnění domény aplikace. To je zvlášť užitečné pro aplikace, které musí být k dispozici průběžně, například ASP.NET lokality.

> [!IMPORTANT]
> Stínové kopírování není podporováno v aplikacích pro Windows 8. x Store.

Modul CLR (Common Language Runtime) zamkne soubor sestavení, když je sestavení načteno, takže soubor nelze aktualizovat, dokud nebude sestavení uvolněno. Jediným způsobem, jak uvolnit sestavení z domény aplikace, je uvolnění domény aplikace, takže za normálních okolností nemůže být sestavení na disku aktualizováno, dokud nebudou všechny domény aplikace, které ji používají, uvolněny.

Když je doména aplikace nakonfigurovaná na soubory stínové kopie, sestavení z cesty aplikace se zkopírují do jiného umístění a načtou z tohoto umístění. Kopie je uzamčena, ale původní soubor sestavení je odemčen a lze jej aktualizovat.

> [!IMPORTANT]
> Pouze sestavení, která lze kopírovat pomocí stínové kopie, jsou uložena v adresáři aplikace nebo v jejích podadresářích, které jsou určeny <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnostmi a při konfiguraci domény aplikace. Sestavení uložená v globální mezipaměti sestavení (GAC) nejsou zkopírována stínem.

Tento článek obsahuje následující oddíly:

- [Povolení a použití stínového kopírování](#EnablingAndUsing) popisuje základní použití a možnosti, které jsou k dispozici pro stínové kopírování.

- [Výkon při spuštění](#StartupPerformance) popisuje změny stínového kopírování v .NET Framework 4 pro zlepšení výkonu při spuštění a postup obnovení na chování starších verzí.

- [Zastaralé metody](#ObsoleteMethods) popisují změny vlastností a metod, které řídí stínové kopírování v .NET Framework 2,0.

<a name="EnablingAndUsing"></a>

## <a name="enabling-and-using-shadow-copying"></a>Povolení a použití stínového kopírování

Můžete použít vlastnosti <xref:System.AppDomainSetup> třídy následujícím způsobem a nakonfigurovat doménu aplikace pro stínové kopírování:

- Povolte stínové kopírování nastavením <xref:System.AppDomainSetup.ShadowCopyFiles%2A> vlastnosti na hodnotu řetězce `"true"` .

  Ve výchozím nastavení toto nastavení způsobí, že všechna sestavení v cestě aplikace budou zkopírována do mezipaměti pro stahování před jejich načtením. Toto je stejná mezipaměť, kterou udržuje modul CLR (Common Language Runtime) pro ukládání souborů stažených z jiných počítačů, a modul CLR (Common Language Runtime) soubory automaticky odstraní, když už nejsou potřeba.

- Volitelně můžete nastavit vlastní umístění pro stínové zkopírované soubory pomocí <xref:System.AppDomainSetup.CachePath%2A> vlastnosti a <xref:System.AppDomainSetup.ApplicationName%2A> Vlastnosti.

  Základní cesta pro umístění je vytvořena zřetězením <xref:System.AppDomainSetup.ApplicationName%2A> vlastnosti s <xref:System.AppDomainSetup.CachePath%2A> vlastností jako podadresářem. Sestavení jsou stínové zkopírovány do podadresářů této cesty, nikoli do samotné základní cesty.

  > [!NOTE]
  > Pokud <xref:System.AppDomainSetup.ApplicationName%2A> vlastnost není nastavena, bude <xref:System.AppDomainSetup.CachePath%2A> vlastnost ignorována a je použita mezipaměť pro stahování. Žádná výjimka se nevyvolá.

  Pokud zadáte vlastní umístění, zodpovídáte za vyčištění adresářů a kopírovaných souborů, pokud už je nepotřebujete. Neodstraňují se automaticky.

  Existuje několik důvodů, proč možná budete chtít nastavit vlastní umístění pro stínové zkopírované soubory. Pokud vaše aplikace generuje velký počet kopií, je vhodné nastavit vlastní umístění pro stínové zkopírované soubory. Mezipaměť pro stahování je omezená velikostí, ne po dobu života, takže je možné, že se modul CLR (Common Language Runtime) pokusí odstranit soubor, který se pořád používá. Dalším důvodem pro nastavení vlastního umístění je, že uživatelé, kteří spouštějí vaši aplikaci, nemají přístup pro zápis do umístění adresáře, které modul CLR (Common Language Runtime) používá pro mezipaměť pro stahování.

- Volitelně můžete omezit sestavení, která jsou Stínová kopie, pomocí <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> Vlastnosti.

  Pokud povolíte stínové kopírování pro doménu aplikace, ve výchozím nastavení se zkopírují všechna sestavení v cestě aplikace – to znamená v adresářích určených <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnostmi a. Kopírování na vybrané adresáře můžete omezit vytvořením řetězce, který obsahuje pouze ty adresáře, ze kterých chcete vytvořit stínovou kopii, a přiřazením řetězce k <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> Vlastnosti. Adresáře oddělte středníkem. Pouze sestavení, která jsou stínové kopie, jsou ta ve vybraných adresářích.

  > [!NOTE]
  > Pokud k vlastnosti nepřiřadíte řetězec <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> nebo pokud tuto vlastnost nastavíte na `null` , jsou stínové kopie všech sestavení v adresářích určených <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> vlastnostmi a.

  > [!IMPORTANT]
  > Cesty k adresáři nesmí obsahovat středník, protože středník je znak oddělovače. Neexistují žádné řídicí znaky pro středníky.

<a name="StartupPerformance"></a>

## <a name="startup-performance"></a>Výkon při spuštění

Když se spustí doména aplikace, která používá stínové kopírování, dojde ke zpoždění během kopírování sestavení v adresáři aplikace do adresáře stínové kopie nebo při ověření, jestli už jsou v tomto umístění. Před .NET Framework 4 byla všechna sestavení zkopírována do dočasného adresáře. Každé sestavení bylo otevřeno pro ověření názvu sestavení a silného názvu bylo ověřeno. Každé sestavení bylo zkontrolováno, zda bylo aktualizováno později než kopírování v adresáři stínové kopie. V takovém případě se zkopíroval do adresáře stínové kopie. Nakonec byly dočasné kopie zahozeny.

Počínaje .NET Framework 4 je výchozí chování při spuštění přímo porovnat datum a čas každého sestavení v adresáři aplikace s datem a časem kopírování v adresáři stínové kopie. Pokud bylo sestavení aktualizováno, je zkopírováno pomocí stejného postupu jako v předchozích verzích .NET Framework; v opačném případě je kopie v adresáři stínové kopie načtena.

Výsledné zlepšení výkonu je největší pro aplikace, ve kterých se sestavení často nemění a změny se většinou vyskytují v malých podmnožině sestavení. Pokud se většina sestavení v aplikaci často mění, může nové výchozí chování způsobit regresi výkonu. Můžete obnovit chování při spuštění předchozích verzí .NET Framework přidáním [ \<shadowCopyVerifyByTimestamp> elementu](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) do konfiguračního souboru pomocí `enabled="false"` .

<a name="ObsoleteMethods"></a>

## <a name="obsolete-methods"></a>Zastaralé metody

<xref:System.AppDomain>Třída má několik metod, například <xref:System.AppDomain.SetShadowCopyFiles%2A> a <xref:System.AppDomain.ClearShadowCopyPath%2A> , které lze použít k řízení stínového kopírování v doméně aplikace, ale ty jsou označeny jako zastaralé ve verzi .NET Framework 2,0. Doporučeným způsobem konfigurace aplikační domény pro stínové kopírování je použití vlastností <xref:System.AppDomainSetup> třídy.

## <a name="see-also"></a>Viz také

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [\<shadowCopyVerifyByTimestamp>Objekt](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
