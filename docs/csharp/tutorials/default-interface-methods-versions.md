---
title: 'Bezpečně aktualizovat rozhraní pomocí výchozích metod rozhraní v C #'
description: Tento pokročilý kurz zkoumá, jak můžete bezpečně přidat nové funkce do existujících definic rozhraní bez porušení všech tříd a struktur, které implementují toto rozhraní.
ms.date: 05/06/2019
ms.technlogy: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 650aea78b421783b3f249b3670578aa60e800ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156776"
---
# <a name="tutorial-update-interfaces-with-default-interface-methods-in-c-80"></a>Kurz: Aktualizace rozhraní s výchozími metodami rozhraní v c# 8.0

Počínaje C# 8.0 na .NET Core 3.0, můžete definovat implementaci při deklarování člena rozhraní. Nejběžnější scénář je bezpečně přidat členy do rozhraní již vydané a používané nesčetnými klienty.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Rozšiřte rozhraní bezpečně přidáním metod s implementacemi.
> * Vytvořte parametrizované implementace, které poskytují větší flexibilitu.
> * Umožněte implementátorům poskytnout konkrétnější implementaci ve formě přepsání.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0. Kompilátor Jazyka C# 8.0 je k dispozici počínaje [visual studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

## <a name="scenario-overview"></a>Přehled scénáře

Tento kurz začíná verzí 1 knihovny vztahů se zákazníky. Můžete získat startovací aplikaci na našich [ukázkách repo na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). Společnost, která vytvořila tuto knihovnu, zamýšlela zákazníky s existujícími aplikacemi, aby přijali svou knihovnu. Poskytly minimální definice rozhraní pro uživatele jejich knihovny k implementaci. Zde je definice rozhraní pro zákazníka:

[!code-csharp[InitialCustomerInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Definovali druhé rozhraní, které představuje pořadí:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Z těchto rozhraní může tým vytvořit knihovnu pro své uživatele, aby vytvořili lepší prostředí pro své zákazníky. Jejich cílem bylo vytvořit hlubší vztah se stávajícími zákazníky a zlepšit jejich vztahy s novými zákazníky.

Nyní je čas na upgrade knihovny pro další verzi. Jedna z požadovaných funkcí umožňuje věrnostní slevu pro zákazníky, kteří mají velké množství objednávek. Tato nová věrnostní sleva se použije vždy, když zákazník provede objednávku. Konkrétní sleva je majetkem každého jednotlivého zákazníka. Každá implementace `ICustomer` může nastavit různá pravidla pro věrnostní slevu.

Nejpřirozenější způsob, jak přidat tuto `ICustomer` funkci je zvýšit rozhraní s metodou použít všechny věrnostní slevy. Tento návrh návrhu vyvolal obavy mezi zkušenými vývojáři: "Rozhraní jsou neměnná, jakmile jsou uvolněna! To je zlomová změna!" C# 8.0 přidává *výchozí implementace rozhraní* pro inovaci rozhraní. Autoři knihovny můžete přidat nové členy do rozhraní a poskytnout výchozí implementaci pro tyto členy.

Výchozí implementace rozhraní umožňují vývojářům upgradovat rozhraní a zároveň umožňují všem implementátorům přepsat tuto implementaci. Uživatelé knihovny mohou přijmout výchozí implementaci jako nenarušující změnu. Pokud se jejich obchodní pravidla liší, mohou je přepsat.

## <a name="upgrade-with-default-interface-methods"></a>Upgrade pomocí výchozích metod rozhraní

Tým se dohodl na nejpravděpodobnější výchozí implementaci: věrnostní slevě pro zákazníky.

Upgrade by měl poskytnout funkce pro nastavení dvou vlastností: počet objednávek potřebných k nároku na slevu a procento slevy. Díky tomu je ideální scénář pro výchozí metody rozhraní. Můžete přidat metodu `ICustomer` do rozhraní a poskytnout nejpravděpodobnější implementaci. Všechny existující a všechny nové implementace můžete použít výchozí implementaci nebo poskytnout své vlastní.

Nejprve přidejte novou metodu k implementaci:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Autor knihovny napsal první test pro kontrolu implementace:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Všimněte si následující části zkoušky:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

To obsazení `SampleCustomer` `ICustomer` od to je nezbytné. Třída `SampleCustomer` nemusí poskytovat implementaci pro `ComputeLoyaltyDiscount`; které je poskytováno `ICustomer` rozhraním. `SampleCustomer` Třída však nedědí členy z jeho rozhraní. To pravidlo se nezměnilo. Chcete-li volat libovolnou metodu deklarovanou a implementovanou `ICustomer` v rozhraní, musí být proměnná typem rozhraní v tomto příkladu.

## <a name="provide-parameterization"></a>Zadat parametrizaci

To je dobrý začátek. Výchozí implementace je však příliš restriktivní. Mnoho spotřebitelů tohoto systému může zvolit různé prahové hodnoty pro počet nákupů, jinou délku členství nebo jinou procentuální slevu. Můžete poskytnout lepší prostředí upgradu pro více zákazníků tím, že poskytuje způsob, jak nastavit tyto parametry. Přidáme statickou metodu, která nastaví tyto tři parametry, které řídí výchozí implementaci:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Existuje mnoho nových jazykových funkcí zobrazených v tomto malém fragmentu kódu. Rozhraní nyní mohou obsahovat statické členy, včetně polí a metod. Jsou také povoleny různé modifikátory přístupu. Další pole jsou soukromá, nová metoda je veřejná. Všechny modifikátory jsou povoleny na členy rozhraní.

Aplikace, které používají obecný vzorec pro výpočet věrnostní slevy, ale různé parametry, není nutné poskytovat vlastní implementaci; mohou nastavit argumenty pomocí statické metody. Například následující kód nastaví "zhodnocení zákazníka", který odměňuje každého zákazníka s více než jeden měsíc členství:

[!code-csharp[SetLoyaltyThresholds](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Rozšíření výchozí implementace

Kód, který jste dosud přidali, poskytl pohodlnou implementaci pro ty scénáře, kde uživatelé chtějí něco jako výchozí implementaci nebo poskytnout nesouvisející sadu pravidel. Pro konečné funkce, pojďme refaktorovat kód bit povolit scénáře, kde uživatelé mohou chtít stavět na výchozí implementaci.

Vezměme si spuštění, které chce přilákat nové zákazníky. Nabízejí 50% slevu z první objednávky nového zákazníka. V opačném případě stávající zákazníci získají standardní slevu. Autor knihovny musí přesunout výchozí `protected static` implementaci do metody tak, aby všechny třídy implementující toto rozhraní můžete znovu použít kód v jejich implementaci. Výchozí implementace člena rozhraní volá také tuto sdílenou metodu:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

V implementaci třídy, která implementuje toto rozhraní, může přepsání volat statickou pomocnou metodu a rozšířit tuto logiku tak, aby poskytovala slevu "nového zákazníka":

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Celý hotový kód můžete vidět v našich [ukázkách repo na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship). Můžete získat startovací aplikaci na našich [ukázkách repo na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship).

Tyto nové funkce znamenají, že rozhraní lze aktualizovat bezpečně, pokud je pro tyto nové členy přiměřená výchozí implementace. Pečlivě navrhněte rozhraní pro vyjádření jednotlivých funkčních nápadů, které mohou být implementovány více třídami. To usnadňuje upgrade těchto definic rozhraní při objevení nových požadavků pro stejnou funkční myšlenku.
