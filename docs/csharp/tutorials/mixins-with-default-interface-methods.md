---
title: Vytváření typů mixinu pomocí výchozích metod rozhraní
description: Pomocí výchozích členů rozhraní můžete rozšířit rozhraní s volitelnými výchozími implementacemi pro implementátory.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: aaf8d34e27c9c56d95560656eb7a7b24b152c053
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240103"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Kurz: Kombinace funkcí při vytváření tříd pomocí rozhraní s výchozími metodami rozhraní

Počínaje C# 8.0 na .NET Core 3.0, můžete definovat implementaci při deklarování člena rozhraní. Tato funkce poskytuje nové funkce, kde můžete definovat výchozí implementace pro funkce deklarované v rozhraních. Třídy můžete vybrat, kdy přepsat funkce, kdy použít výchozí funkce a kdy nedeklarovat podporu pro diskrétní funkce.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvořte rozhraní s implementacemi, které popisují diskrétní funkce.
> * Vytvořte třídy, které používají výchozí implementace.
> * Vytvořte třídy, které přepíší některé nebo všechny výchozí implementace.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0. Kompilátor Jazyka C# 8.0 je k dispozici počínaje [visual studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější.

## <a name="limitations-of-extension-methods"></a>Omezení rozšiřujících metod

Jedním ze způsobů, jak můžete implementovat chování, které se zobrazí jako součást rozhraní je definovat [metody rozšíření,](../programming-guide/classes-and-structs/extension-methods.md) které poskytují výchozí chování. Rozhraní deklarovat minimální sadu členů a zároveň poskytuje větší plochu pro všechny třídy, která implementuje toto rozhraní. Například metody rozšíření <xref:System.Linq.Enumerable> v poskytují implementaci pro všechny sekvence být zdrojem dotazu LINQ.

Rozšiřující metody jsou vyřešeny v době kompilace pomocí deklarovaného typu proměnné. Třídy, které implementují rozhraní může poskytnout lepší implementaci pro všechny metody rozšíření. Deklarace proměnných musí odpovídat implementujícímu typu, aby kompilátor mohl tuto implementaci zvolit. Když typ kompilace odpovídá rozhraní, volání metody přeložit metodu rozšíření. Další obavou s metodami rozšíření je, že tyto metody jsou přístupné všude tam, kde je přístupná třída obsahující metody rozšíření. Třídy nelze deklarovat, pokud by měly nebo neměly poskytovat funkce deklarované v metodách rozšíření.

Počínaje C# 8.0, můžete deklarovat výchozí implementace jako metody rozhraní. Potom každá třída automaticky používá výchozí implementaci. Každá třída, která může poskytnout lepší implementaci, může přepsat definici metody rozhraní pomocí lepšího algoritmu. V jistém smyslu tato technika zní podobně jako jak byste mohli použít [metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md).

V tomto článku se dozvíte, jak výchozí implementace rozhraní umožňují nové scénáře.

## <a name="design-the-application"></a>Návrh aplikace

Zvažte aplikaci domácí automatizace. Pravděpodobně máte mnoho různých typů světel a indikátorů, které by mohly být použity v celém domě. Každé světlo musí podporovat api je zapnout a vypnout a hlásit aktuální stav. Některá světla a indikátory mohou podporovat další funkce, například:

- Zapněte světlo a po časovači jej vypněte.
- Po určitou dobu zabližte světlem.

Některé z těchto rozšířených funkcí by mohly být emulovány v zařízeních, která podporují minimální sadu. To znamená, že poskytuje výchozí implementaci. Pro zařízení, která mají více vestavěných funkcí, by software zařízení používal nativní funkce. Pro ostatní světla mohou zvolit implementaci rozhraní a použít výchozí implementaci.

Výchozí členové rozhraní je lepší řešení pro tento scénář než metody rozšíření. Autoři třídy mohou řídit, která rozhraní se rozhodnou implementovat. Tato rozhraní, která zvolí, jsou k dispozici jako metody. Kromě toho protože výchozí metody rozhraní jsou virtuální ve výchozím nastavení, expedice metody vždy zvolí implementaci ve třídě.

Pojďme vytvořit kód k předvedení těchto rozdílů.

## <a name="create-interfaces"></a>Vytváření rozhraní

Začněte vytvořením rozhraní, které definuje chování pro všechna světla:

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Základní stropní svítidlo může implementovat toto rozhraní, jak je znázorněno v následujícím kódu:

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

V tomto kurzu kód neřídí zařízení IoT, ale emuluje tyto aktivity zápisem zpráv do konzoly. Můžete prozkoumat kód bez automatizace vašeho domu.

Dále definujme rozhraní pro světlo, které se může automaticky vypnout po časovém odnoži:

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Můžete přidat základní implementaci na kontrolku režie, ale lepším řešením je `virtual` upravit tuto definici rozhraní tak, aby poskytovala výchozí implementaci:

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Přidáním této změny `OverheadLight` může třída implementovat funkci časovače deklarováním podpory rozhraní:

```csharp
public class OverheadLight : ITimerLight { }
```

Jiný typ světla může podporovat sofistikovanější protokol. Může poskytnout vlastní implementaci `TurnOnFor`pro , jak je znázorněno v následujícím kódu:

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

Na rozdíl od přepsání `TurnOnFor` metody `HalogenLight` virtuální třídy `override` deklarace ve třídě nepoužívá klíčové slovo.

## <a name="mix-and-match-capabilities"></a>Kombinovat možnosti

Výhody výchozích metod rozhraní se stávají jasnějšími, když zavádíte pokročilejší funkce. Pomocí rozhraní umožňuje kombinovat možnosti. Umožňuje také každému autorovi třídy vybrat si mezi výchozí implementací a vlastní implementací. Přidáme rozhraní s výchozí implementací pro blikající světlo:

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

Výchozí implementace umožňuje blikání libovolného světla. Kontrolka nad hlavou může přidat časovač i funkce blikání pomocí výchozí implementace:

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Nový typ světla, `LEDLight` podporuje jak funkci časovače, tak funkci bliknutí přímo. Tento styl světla implementuje `ITimerLight` rozhraní a `IBlinkingLight` rozhraní `Blink` a přepíše metodu:

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

Funkce `ExtraFancyLight` může podporovat funkce blikání i časovače přímo:

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

Dříve `HalogenLight` vytvořené vytvořené nepodporuje blikání. Takže nepřidávejte `IBlinkingLight` seznam podporovaných rozhraní.

## <a name="detect-the-light-types-using-pattern-matching"></a>Detekce typů světel pomocí přizpůsobení vzoru

Dále napíšeme nějaký testovací kód. Můžete použít c# vzor [odpovídající](../pattern-matching.md) funkce k určení světla schopnosti kontrolou, která rozhraní podporuje.  Následující metoda vykonává podporované schopnosti každého světla:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Následující kód v `Main` metodě vytvoří každý typ světla v pořadí a testuje, že světlo:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Jak kompilátor určuje nejlepší implementaci

Tento scénář zobrazuje základní rozhraní bez implementace. Přidání metody do `ILight` rozhraní zavádí nové složitosti. Pravidla jazyka, kterými se řídí metody výchozí rozhraní minimalizovat vliv na konkrétní třídy, které implementují více odvozených rozhraní. Vylepšeme původní rozhraní novou metodou, která ukáže, jak to změní jeho použití. Každá kontrolka může vykazovat stav napájení jako vyčíslenou hodnotu:

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

Výchozí implementace předpokládá napájení střídavého proudu:

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Tyto změny zkompilovat `ExtraFancyLight` čistě, i `ILight` když deklaruje `ITimerLight` podporu `IBlinkingLight`pro rozhraní a obě odvozené rozhraní a . V `ILight` rozhraní je deklarována pouze jedna "nejbližší" implementace. Každá třída, která deklarovala přepsání by se stala "nejbližší" implementací. Viděli jste příklady v předchozích třídách, které převyšují členy jiných odvozených rozhraní.

Vyhněte se přepsání stejné metody ve více odvozených rozhraních. Tím se vytvoří volání nejednoznačné metody vždy, když třída implementuje obě odvozená rozhraní. Kompilátor nemůže vybrat jednu lepší metodu, takže vydá chybu. Například pokud oba `IBlinkingLight` `ITimerLight` a implementované `PowerStatus`přepsání , `OverheadLight` bude muset poskytnout konkrétnější přepsání. V opačném případě kompilátor nelze vybrat mezi implementacemi ve dvou odvozených rozhraních. Obvykle se můžete vyhnout této situaci udržováním definice rozhraní malé a zaměřené na jednu funkci. V tomto scénáři každá schopnost světla je jeho vlastní rozhraní; více rozhraní jsou zděděny pouze třídy.

Tato ukázka ukazuje jeden scénář, kde můžete definovat diskrétní funkce, které mohou být smíchány do tříd. Deklarujete libovolnou sadu podporovaných funkcí deklarováním, která rozhraní třída podporuje. Použití virtuálních výchozích metod rozhraní umožňuje třídám používat nebo definovat jinou implementaci pro některé nebo všechny metody rozhraní. Tato jazyková funkce poskytuje nové způsoby modelování reálných systémů, které vytváříte. Výchozí metody rozhraní poskytují jasnější způsob, jak vyjádřit související třídy, které mohou kombinovat různé funkce pomocí virtuálníimplementace těchto funkcí.
