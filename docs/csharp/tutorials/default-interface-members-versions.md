---
title: Bezpečně aktualizace pomocí výchozího členy rozhraní v rozhraníC#
description: Tento kurz pokročilé zkoumá, jak můžete bezpečně přidávat nové funkce do existující definice rozhraní bez narušení všechny třídy a struktury, které implementují rozhraní.
ms.date: 05/06/2019
ms.custom: mvc
ms.openlocfilehash: 2daa40ead5902454c6d45390233e1491fe6d369b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877908"
---
# <a name="tutorial-update-interfaces-with-default-interface-members-in-c-80"></a>Kurz: Aktualizovat výchozí členy rozhraní v rozhraní C# 8.0

Počínaje C# 8.0 na .NET Core 3.0, můžete definovat implementaci při deklaraci člena rozhraní. Nejběžnější scénář je bezpečně přidávat členy do rozhraní už vydali a používají klienti innumerable.

V tomto kurzu se dozvíte jak:

> [!div class="checklist"]
> * Bezpečně rozšiřte rozhraní přidáním metod s implementací.
> * Vytvoření parametrizovaných implementace poskytují větší flexibilitu.
> * Umožňují implementátorům k dispozici konkrétnější implementace v podobě přepsání.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně C# kompilátoru 8.0 ve verzi preview. C# 8.0 kompilátoru ve verzi preview je k dispozici počínaje [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), nebo si prohlédnout nejnovější [.NET Core 3.0 ve verzi preview SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0). Výchozí členy rozhraní jsou k dispozici od verze .NET Core 3.0 ve verzi preview 4.

## <a name="scenario-overview"></a>Přehled scénářů

Tento kurz pracuje s verzí 1 knihovnu vztah zákazníků. Startovní aplikace můžete získat naše [úložišti na Githubu ukázky](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). Společnost, která je vytvořená tuto knihovnu určené zákazníkům se stávajícími aplikacemi a přijmout jejich knihovny. Poskytnou definice minimální rozhraní pro uživatele jejich knihovny k implementaci. Tady je definice rozhraní pro zákazníka:

[!code-csharp[InitialCustomerInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Jsou definovány druhé rozhraní, která představuje pořadí:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Z těchto rozhraní může tým sestavení knihovny pro jejich uživatelům vytvářet lepší prostředí pro zákazníky. Jeho cílem bylo vytvořit podrobnější relaci se stávající zákazníky a zvýšit jejich vztahy s novým zákazníkům.

Nyní je doba pro upgrade knihovny pro další verzi. Mezi požadované funkce pro zákazníky, kteří mají velké množství objednávek umožňuje slevu věrnostních programů. Tento nový věrnostní získá sleva pokaždé, když zákazník zadá objednávku. Konkrétní sleva je vlastnost pro každého zákazníka. Každá implementace ICustomer můžete nastavit různá pravidla slevu věrnostních programů. 

Většina přirozený způsob, jak přidat tato funkce je k vylepšení `ICustomer` rozhraní se způsob, jak použít případné slevy věrnostních programů. Tento návrh návrh způsobila problém mezi zkušené vývojáře: "Rozhraní jsou neměnné, když jsme vydali! Toto je zásadní změnu." C#Přidá 8.0 *výchozí implementace rozhraní* pro upgrade rozhraní. Autoři knihovny můžete přidat nové členy rozhraní a poskytuje výchozí implementaci pro ty členy.

Výchozí implementace rozhraní umožňují vývojářům upgrade rozhraní ale žádné implementors pro tuto implementaci přepsat. Uživatelé knihovny můžete přijmout výchozí implementace jako nevýznamných změn. Pokud se liší jejich obchodních pravidel, můžete přepsat.

## <a name="upgrade-with-default-interface-members"></a>Upgrade s výchozí členy rozhraní

Tým dohodl na maximum pravděpodobně výchozí implementace: slevu loajalitu zákazníků.

Upgrade by zajišťovat funkce můžete nastavit dvě vlastnosti: počet objednávek, které jsou potřebné k dosažení nárok slevu a procento slevy. Díky tomu je ideální scénář pro členy výchozí rozhraní. Můžete přidat metodu rozhraní ICustomer a pravděpodobně implementaci. Všechny existující a všechny nové implementace můžete použít výchozí implementace nebo zadat vlastní.

Nejprve přidejte nové metody pro implementaci:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Autor knihovny napsal prvního testu ke kontrole implementace:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Všimněte si následující část testu:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

Který přetypování z `SampleCustomer` k `ICustomer` je nezbytné. `SampleCustomer` Třídy nemusí poskytovat implementaci pro `ComputeLoyaltyDiscount`; který poskytuje `ICustomer` rozhraní. Ale `SampleCustomer` Třída nedědí členy z jeho rozhraní. Toto pravidlo se nezměnil. Aby bylo možné volat jakékoli metodu deklarovat a implementovat rozhraní, musí být proměnná typu rozhraní, `ICustomer` v tomto příkladu.

## <a name="provide-parameterization"></a>Zadejte Parametrizace

To je dobrý začátek. Ale výchozí implementace je příliš omezující. Mnoho příjemci tohoto systému rozhodnout různé prahové hodnoty pro číslo nákupy, jinou délku členství nebo jiné procento slevy. Pro větší počet zákazníků tím, že poskytuje způsob, jak nastavit tyto parametry můžete zadat lepší prostředí pro upgrade. Přidejme statická metoda, která nastaví tyto tři parametry řízení výchozí implementace:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Existuje mnoho nových funkcí jazyka uvedené v tomto fragmentu malý kód. Rozhraní teď může obsahovat statické členy, včetně polí a metod. Modifikátory přístupu různých jsou také povoleny. Další pole jsou privátní, nová metoda je veřejná. Pro členy rozhraní jsou povoleny žádné modifikátory.

Aplikace, které používají obecné vzorce pro výpočet věrnostní slevy, ale jiné parametry, není potřeba zadávat vlastní implementaci; argumenty, můžete nastavit pomocí statické metody. Například následující kód nastaví "zákazník zhodnocení", který odměňuje každý zákazník s více než jeden měsíc členství:

[!code-csharp[SetLoyaltyThresholds](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Rozšířit výchozí implementace

Kód, který jste přidali zatím poskytuje praktické implementace pro tyto scénáře, ve kterém uživatelé chtějí něco jako výchozí implementace nebo k poskytování nesouvisející sady pravidel. Poslední funkci Pojďme Refaktorovat kód o něco k povolení scénářů, kde mohou uživatelé chtějí na výchozí implementaci. 

Vezměte v úvahu při spuštění, který chce, aby se umožnilo přilákat nové zákazníky. Nabízejí 50 % slevu z první pořadí nového zákazníka. V opačném případě stávající zákazníci získat standardní slevy. Autor knihovny se musí přesunout do výchozí implementace `protected static` metodu tak, že třída implementace tohoto rozhraní můžete opakovaně používat kód v jejich provádění. Výchozí implementace členů rozhraní volá tuto sdílenou metodu:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

V implementaci třídy, která implementuje toto rozhraní, přepsání můžete volat metodu statické pomocné rutiny a rozšířit tuto logiku pro poskytování "nového zákazníka" slevy:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Zobrazí celý Dokončený kód v našich [ukázky úložišti na Githubu] (Startovní aplikace můžete získat naše [úložišti na Githubu ukázky](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship).

Tyto nové funkce znamená, že rozhraní můžete aktualizovat bezpečně po implementaci přiměřené výchozí hodnoty pro nové členy. Pečlivě Navrhněte rozhraní express jeden funkční nápady, které může být implementována více tříd. Který usnadňuje upgradovat tyto definice rozhraní při zjištění nových požadavků pro tento stejný funkční nápad.
