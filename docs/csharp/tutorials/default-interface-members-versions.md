---
title: Bezpečně aktualizovat rozhraní pomocí výchozích členů rozhraní vC#
description: V tomto rozšířeném kurzu se seznámíte s tím, jak můžete bezpečně přidat nové funkce do stávajících definic rozhraní bez přerušení všech tříd a struktur, které implementují toto rozhraní.
ms.date: 05/06/2019
ms.custom: mvc
ms.openlocfilehash: 6a723a116d420dd43d2adeef98b824445dd4f0d7
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926706"
---
# <a name="tutorial-update-interfaces-with-default-interface-members-in-c-80"></a>Kurz: Aktualizace rozhraní s výchozími členy rozhraní C# v 8,0

Počínaje C# 8,0 na .net Core 3,0 můžete definovat implementaci při deklaraci člena rozhraní. Nejběžnějším scénářem je bezpečné přidání členů do rozhraní, které již bylo uvolněno a používáno klienty nespočet.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Bezpečnější rozšíření rozhraní přidáním metod s implementacemi.
> * Vytváření parametrizovaných implementací k zajištění větší flexibility.
> * Povolit implementátorům poskytnutí konkrétnější implementace ve formě přepsání.

## <a name="prerequisites"></a>Požadavky

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru verze C# 8,0 Preview. Kompilátor C# verze Preview 8,0 je k dispozici počínaje verzí [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo nejnovější [sadou .NET Core 3,0 Preview SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0). Výchozí členové rozhraní jsou k dispozici od verze .NET Core 3,0 Preview 4.

## <a name="scenario-overview"></a>Přehled scénáře

Tento kurz začíná verzí 1 knihovny vztahů se zákazníky. Úvodní aplikaci můžete získat na našem [úložišti ukázek na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). Společnost, která vytvořila tuto knihovnu, určila zákazníky, kteří mají existující aplikace k přijetí své knihovny. Poskytovaly minimální definice rozhraní pro uživatele své knihovny k implementaci. Tady je definice rozhraní pro zákazníka:

[!code-csharp[InitialCustomerInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Definují druhé rozhraní, které představuje objednávku:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Z těchto rozhraní může tým sestavit knihovnu pro své uživatele a vytvořit tak lepší prostředí pro své zákazníky. Jejich cílem bylo vytvoření hlubšího vztahu se stávajícími zákazníky a vylepšení jejich vztahů s novými zákazníky.

Teď je čas upgradovat knihovnu pro další verzi. Jedna z požadovaných funkcí umožňuje zákazníkům, kteří mají spoustu objednávek, věrnostní slevu. Tato nová věrnostní sleva se použije vždy, když zákazník provede objednávku. Konkrétní sleva je vlastnost každého jednotlivého zákazníka. Každá implementace `ICustomer` nástroje může nastavit jiná pravidla pro věrnostní slevu. 

Nejpřirozenější způsob, jak tuto funkci přidat, je vylepšit `ICustomer` rozhraní s metodou pro použití věrnostní slevy. Tento návrh návrhu způsobil obavy mezi zkušenými vývojáři: "Rozhraní jsou po vydání proměnlivá. Toto je zásadní změna. " C#8,0 přidává *výchozí implementaci rozhraní* pro upgrade rozhraní. Autoři knihovny mohou přidat nové členy do rozhraní a poskytnout výchozí implementaci pro tyto členy.

Implementace výchozích rozhraní umožňují vývojářům upgradovat rozhraní a zároveň přitom povolit jakékoli implementátory k přepsání této implementace. Uživatelé knihovny mohou přijmout výchozí implementaci jako neprůlomou změnu. Pokud jsou jejich obchodní pravidla odlišná, můžou je přepsat.

## <a name="upgrade-with-default-interface-members"></a>Upgrade s výchozími členy rozhraní

Tým se dohodl s nejpravděpodobnější výchozí implementací: věrnostní sleva pro zákazníky.

Upgrade by měl poskytovat funkce pro nastavení dvou vlastností: počet objednávek potřebných k poskytnutí slevy a procento slevy. Díky tomu je ideální scénář pro výchozí členy rozhraní. Do `ICustomer` rozhraní můžete přidat metodu a poskytnout nejpravděpodobnější implementaci. Všechny stávající a jakékoli nové implementace mohou použít výchozí implementaci nebo zadat vlastní.

Nejdřív přidejte do implementace novou metodu:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Autor knihovny napsal první test pro kontrolu implementace:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Všimněte si následující části testu:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

Přetypování z `SampleCustomer` na `ICustomer` je nezbytné. Třída nemusí poskytovat implementaci pro `ComputeLoyaltyDiscount`, `ICustomer` která je poskytována rozhraním. `SampleCustomer` `SampleCustomer` Třída však nedědí členy z jeho rozhraní. Toto pravidlo se nezměnilo. Aby bylo možné volat jakoukoli metodu deklarovanou a implementovanou v rozhraní, proměnná musí být typu rozhraní, `ICustomer` v tomto příkladu.

## <a name="provide-parameterization"></a>Poskytněte Parametrizace

To je dobrý začátek. Výchozí implementace je ale příliš omezující. Mnoho uživatelů tohoto systému může zvolit různé prahové hodnoty pro počet nákupů, jinou délku členství nebo jinou procentní slevu. Můžete zajistit lepší prostředí pro upgrade pro více zákazníků tím, že poskytnete způsob, jak tyto parametry nastavit. Pojďme přidat statickou metodu, která nastaví tyto tři parametry, které řídí výchozí implementaci:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

V této malém fragmentu kódu je zobrazený velký počet nových možností jazyka. Rozhraní teď můžou zahrnovat statické členy, včetně polí a metod. Jsou povolené taky různé modifikátory přístupu. Další pole jsou soukromá, nová metoda je veřejná. Všechny modifikátory jsou povoleny u členů rozhraní.

Aplikace, které používají obecný vzorec pro výpočet věrnostní slevy, ale jiné parametry, nepotřebují zadat vlastní implementaci; mohou nastavovat argumenty prostřednictvím statické metody. Například následující kód nastaví "zhodnocení zákazníka", které vyměňuje každého zákazníka s více než jedním měsícem členství:

[!code-csharp[SetLoyaltyThresholds](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Rozšiřování výchozí implementace

Kód, který jste dosud přidali, měl k dispozici pohodlnou implementaci pro tyto scénáře, kde uživatelé mají něco podobného jako výchozí implementace, nebo poskytnutí nesouvisející sady pravidel. Pro závěrečnou funkci můžeme kód trochu přefaktorovat, aby bylo možné povolit scénáře, kde mohou uživatelé chtít sestavit výchozí implementaci. 

Vezměte v úvahu spuštění, které chce přilákat nové zákazníky. Nabízí 50% slevu od prvního pořadí nového zákazníka. V opačném případě stávající zákazníci získají standardní slevu. Autor knihovny musí přesunout výchozí implementaci do `protected static` metody, aby jakákoliv třída implementující toto rozhraní mohla znovu použít kód v jejich implementaci. Výchozí implementace člena rozhraní volá i tuto sdílenou metodu:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

V implementaci třídy, která implementuje toto rozhraní, může přepsání zavolat statickou pomocnou metodu a tuto logiku zvětšit tak, aby poskytovala slevu "novému zákazníkovi":

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Celý dokončený kód můžete zobrazit v našem [úložišti ukázek na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship). Úvodní aplikaci můžete získat na našem [úložišti ukázek na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship).

Tyto nové funkce znamenají, že rozhraní je možné bezpečně aktualizovat, pokud existuje přiměřená výchozí implementace pro tyto nové členy. Pečlivě Navrhněte rozhraní pro vyjádření jednoduchých funkčních nápadů, které mohou být implementovány více třídami. To usnadňuje upgrade těchto definic rozhraní, když jsou zjištěny nové požadavky pro stejný funkční nápad.
