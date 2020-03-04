---
title: Vytváření Mixin typů pomocí výchozích metod rozhraní
description: Pomocí výchozích členů rozhraní můžete roztáhnout rozhraní s nepovinnými výchozími implementacemi pro implementátory.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: aaf8d34e27c9c56d95560656eb7a7b24b152c053
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240103"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Kurz: kombinace funkcí při vytváření tříd pomocí rozhraní s výchozími metodami rozhraní

Počínaje C# 8,0 na .net Core 3,0 můžete definovat implementaci při deklaraci člena rozhraní. Tato funkce poskytuje nové funkce, kde můžete definovat výchozí implementace pro funkce deklarované v rozhraních. Třídy mohou vybírat, kdy přepsat funkce, kdy použít výchozí funkce a kdy není deklarována podpora diskrétních funkcí.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * Vytvořte rozhraní s implementacemi, které popisují diskrétní funkce.
> * Vytvořte třídy, které používají výchozí implementace.
> * Vytvořte třídy, které přepíší některé nebo všechny výchozí implementace.

## <a name="prerequisites"></a>Předpoklady

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0. Kompilátor C# 8,0 je k dispozici počínaje [verzí Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější.

## <a name="limitations-of-extension-methods"></a>Omezení metod rozšíření

Jedním ze způsobů, jak můžete implementovat chování, které se zobrazí jako součást rozhraní, je definovat [metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md) , které poskytují výchozí chování. Rozhraní deklaruje minimální sadu členů a současně poskytují větší plochu pro jakoukoliv třídu, která implementuje toto rozhraní. Například metody rozšíření v <xref:System.Linq.Enumerable> poskytují implementaci pro jakékoli sekvenci jako zdroj dotazu LINQ.

Metody rozšíření jsou vyřešeny v době kompilace pomocí deklarovaného typu proměnné. Třídy, které implementují rozhraní, mohou poskytovat lepší implementaci libovolné metody rozšíření. Deklarace proměnných musí odpovídat implementující typu, aby mohl kompilátor zvolit tuto implementaci. Když typ doby kompilace odpovídá rozhraní, volání metody se překládají na metodu rozšíření. Dalším problémem s rozšiřujícími metodami je, že tyto metody jsou přístupné všude, kde je přístupná třída obsahující metody rozšíření. Třídy nemohou deklarovat, pokud by měly nebo by neměly poskytovat funkce deklarované v metodách rozšíření.

Počínaje C# 8,0 můžete deklarovat výchozí implementace jako metody rozhraní. Pak každá třída automaticky používá výchozí implementaci. Libovolná třída, která může poskytnout lepší implementaci, může přepsat definici metody rozhraní s lepším algoritmem. V jednom smyslu Tato technika popisuje, jak můžete použít [rozšiřující metody](../programming-guide/classes-and-structs/extension-methods.md).

V tomto článku se dozvíte, jak výchozí implementace rozhraní povolují nové scénáře.

## <a name="design-the-application"></a>Návrh aplikace

Zvažte možnost domácí aplikace automatizace. Pravděpodobně máte mnoho různých typů světel a indikátorů, které by mohly být použity v celém domu. Každé světlo musí podporovat rozhraní API, aby je bylo možné zapnout a vypnout a ohlásit aktuální stav. Některé světla a indikátory mohou podporovat jiné funkce, jako například:

- Zapnout světlo a pak ho vypnout po vypršení časového časovače.
- Rozsvítit světlo v časovém intervalu.

Některé z těchto rozšířených funkcí by mohly být emulované v zařízeních, která podporují minimální sadu. Který označuje, že je zajištěna výchozí implementace. Pro ta zařízení, která mají integrované další možnosti, používá software zařízení nativní možnosti. Pro ostatní světla by mohli zvolit implementaci rozhraní a použití výchozí implementace.

Výchozí členy rozhraní představují lepší řešení pro tento scénář než metody rozšíření. Autoři tříd mohou řídit, která rozhraní budou chtít implementovat. Tato rozhraní, která zvolí, jsou k dispozici jako metody. Kromě toho, protože výchozí metody rozhraní jsou ve výchozím nastavení virtuální, metoda odeslání vždy zvolí implementaci ve třídě.

Pojďme vytvořit kód, abychom předvedli tyto rozdíly.

## <a name="create-interfaces"></a>Vytvoření rozhraní

Začněte vytvořením rozhraní, které definuje chování pro všechny světla:

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Základní přípojka režie by mohla implementovat toto rozhraní, jak je znázorněno v následujícím kódu:

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

V tomto kurzu kód neřídí zařízení IoT, ale emuluje tyto aktivity zápisem zpráv do konzoly. Kód můžete prozkoumat bez automatizace vaší domu.

Nyní nadefinujte rozhraní pro světlo, které se může automaticky vypnout po vypršení časového limitu:

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Můžete přidat základní implementaci do režijního světla, ale lepším řešením je upravit tuto definici rozhraní a poskytnout `virtual` výchozí implementaci:

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Přidáním této změny může třída `OverheadLight` implementovat funkci časovače tím, že deklaruje podporu rozhraní:

```csharp
public class OverheadLight : ITimerLight { }
```

Jiný typ světla může podporovat propracovanější protokol. Může poskytnout svou vlastní implementaci pro `TurnOnFor`, jak je znázorněno v následujícím kódu:

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

Na rozdíl od přepisu metod virtuální třídy nepoužívá deklarace `TurnOnFor` ve třídě `HalogenLight` klíčové slovo `override`.

## <a name="mix-and-match-capabilities"></a>Možnosti kombinace a shody

Výhody výchozích metod rozhraní se při zavádění pokročilejších funkcí stanou nejasnější. Používání rozhraní umožňuje kombinovat a odpovídat možnostem. Umožňuje také každému autorovi třídy zvolit mezi výchozí implementací a vlastní implementací. Pojďme přidat rozhraní s výchozí implementací pro blikající světlo:

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

Výchozí implementace umožňuje jakékoli světlo blikat. Režijní náklady mohou pomocí výchozí implementace přidat možnosti časovače i blikání:

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Nový typ světla, `LEDLight` podporuje přímo funkci Timer i funkci Blink. Tento styl světla implementuje rozhraní `ITimerLight` i `IBlinkingLight` a přepisuje metodu `Blink`:

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

`ExtraFancyLight` může podporovat funkce blikání i časovače přímo:

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

`HalogenLight`, který jste vytvořili dříve, nepodporuje blikání. Nepřidejte `IBlinkingLight` do seznamu podporovaných rozhraní.

## <a name="detect-the-light-types-using-pattern-matching"></a>Detekovat světlo typy pomocí porovnávání vzorů

Nyní napíšeme nějaký testovací kód. Můžete využít C#funkci [porovnávání vzorů](../pattern-matching.md) k určení možností světla tím, že prozkoumáte, která rozhraní podporuje.  Následující metoda využije podporované funkce každého světla:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Následující kód v metodě `Main` vytvoří každý typ světla v sekvenci a provede testy, které světlo:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Způsob, jakým kompilátor určí nejlepší implementaci

Tento scénář ukazuje základní rozhraní bez implementace. Přidání metody do rozhraní `ILight` zavádí nové složitosti. Jazyková pravidla řízení výchozích metod rozhraní minimalizují vliv na konkrétní třídy, které implementují více odvozených rozhraní. Pojďme vylepšit původní rozhraní novou metodou, která ukazuje, jak se tyto změny použijí. Každé světlo indikátor může hlásit svůj stav napájení jako výčtovou hodnotu:

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

Výchozí implementace předpokládá napájení z elektrické sítě:

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Tyto změny se zkompiluje čistě, i když `ExtraFancyLight` deklaruje podporu rozhraní `ILight` a obou odvozených rozhraní, `ITimerLight` a `IBlinkingLight`. V rozhraní `ILight` je deklarována pouze jedna "nejbližší" implementace. Jakákoliv třída, která deklarovaná přepsání by se stala jedinou implementací "nejbližší". Viděli jste příklady v předchozích třídách, které overrode členy jiných odvozených rozhraní.

Vyhněte se přepsání stejné metody ve více odvozených rozhraních. Tím se vytvoří dvojznačné volání metody vždy, když třída implementuje jak odvozená rozhraní. Kompilátor nemůže vybrat jedinou lepší metodu, takže dojde k chybě. Například pokud `IBlinkingLight` i `ITimerLight` implementovaly přepsání `PowerStatus`, `OverheadLight` by musel poskytnout konkrétnější přepsání. V opačném případě kompilátor nemůže vybírat mezi implementacemi ve dvou odvozených rozhraních. Tuto situaci lze obvykle vyhnout tím, že zachováte definice rozhraní v malém a zaměření na jednu funkci. V tomto scénáři je každá schopnost světla jeho vlastním rozhraním; více rozhraní dědí pouze třídy.

Tento příklad ukazuje jeden scénář, kde můžete definovat diskrétní funkce, které mohou být smíchány do tříd. Deklarujete jakoukoli sadu podporovaných funkcí tím, že deklarujete, která rozhraní podporuje třída. Použití virtuálních výchozích metod rozhraní umožňuje třídám použít nebo definovat odlišnou implementaci pro jakékoli nebo všechny metody rozhraní. Tato funkce jazyka poskytuje nové způsoby modelování reálných systémů, které vytváříte. Výchozí metody rozhraní poskytují jasný způsob, jak vyjádřit související třídy, které se mohou kombinovat a porovnat s různými funkcemi pomocí virtuálních implementací těchto schopností.
