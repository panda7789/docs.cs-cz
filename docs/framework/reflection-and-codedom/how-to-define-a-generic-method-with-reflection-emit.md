---
title: 'Postupy: Definování obecné metody pomocí generování reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic methods
- generics [.NET Framework], dynamic types
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a224093b47241d951b463a7f3e0be389bba2806
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043729"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Postupy: Definování obecné metody pomocí generování reflexe

První procedura ukazuje, jak vytvořit jednoduchou obecnou metodu se dvěma parametry typu a jak použít omezení třídy, omezení rozhraní a zvláštní omezení pro parametry typu.

Druhý postup ukazuje, jak vygenerovat tělo metody, jak používat parametry typu obecné metody k vytvoření instance obecných typů a jak volat jejich metody.

Třetí postup ukazuje, jak zavolat obecnou metodu.

> [!IMPORTANT]
> Metoda není obecná jen proto, že patří obecnému typu a používá parametry typu daného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. Obecná metoda se může objevit v neobecném typu, jako je tomu v následujícím příkladu. Příklad neobecné metody na obecném typu naleznete v tématu [How to: Definujte obecný typ pomocí generování](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)reflexe.

### <a name="to-define-a-generic-method"></a>Definice obecné metody

1. Než začnete, je užitečné si prohlédnout, jak obecná metoda vypadá, když je napsána pomocí jazyka vysoké úrovně. Následující kód je zahrnut v příkladu kódu pro toto téma spolu s kódem pro volání obecné metody. Metoda má dva parametry typu `TInput` a `TOutput`, druhý z nich musí být odkazovým typem (`class`), musí mít konstruktor bez parametrů (`new`) a musí implementovat rozhraní `ICollection(Of TInput)` (`ICollection<TInput>` v jazyce C#). Toto omezení rozhraní zajišťuje, že metodu <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> lze použít k přidání prvků do kolekce `TOutput`, kterou metoda vytvoří. Tato metoda má jeden formální parametr `input`, což je pole `TInput`. Metoda vytvoří kolekci typu `TOutput` a zkopíruje prvky parametru `input` do této kolekce.

    [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
    [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]

2. Definujte dynamické sestavení a dynamický modul obsahující typ, ke kterému tato obecná metoda patří. V tomto případě má sestavení pouze jeden modul s názvem `DemoMethodBuilder1` a název tohoto modulu je stejný jako název sestavení s příponou souboru. V tomto příkladu je sestavení uloženo na disk a také spuštěno, takže je zadáno <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType>. Nástroj [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) můžete použít k prohlédnutí souboru DemoMethodBuilder1. dll a k jeho porovnání do jazyka MSIL (Microsoft Intermediate Language) pro metodu, která je znázorněna v kroku 1.

    [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
    [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]

3. Definujte typ, ke kterému obecná metoda patří. Tento typ nemusí být obecný. Obecná metoda může patřit obecnému nebo neobecnému typu. V příkladu je tento typ třída, není obecná a má název `DemoType`.

    [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
    [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]

4. Definujte obecnou metodu. Pokud jsou typy formálních parametrů obecné metody určeny parametry obecného typu obecné metody, použijte přetížení metody <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> k definici této metody. Parametry obecného typu metody nejsou ještě definovány, proto nelze určit typy formálních parametrů metody při volání metody <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>. Metoda v tomto příkladu je pojmenována `Factory`. Tato metoda je veřejná a deklarovaná jako `static` (`Shared` v jazyce Visual Basic).

    [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
    [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]

5. Definujte parametry obecného typu metody `DemoMethod` předáním pole řetězců obsahujícího názvy parametrů metodě <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType>. To tuto metodu učiní obecnou metodou. Následující kód učiní metodu `Factory` obecnou metodou s parametry typu `TInput` a `TOutput`. Pro usnadnění čtení kódu jsou vytvořeny proměnné s těmito názvy pro uchování objektů <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, které představují dva parametry typu.

    [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
    [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]

6. Volitelně lze těmto parametrům typu přidat zvláštní omezení. Zvláštní omezení jsou přidána pomocí metody <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A>. V tomto příkladu je parametr `TOutput` omezen na odkazový typ a musí mít konstruktor bez parametrů.

    [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
    [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]

7. Volitelně lze těmto parametrům typu přidat omezení rozhraní a třídy. V tomto příkladu je parametr typu `TOutput` omezen na typy, které implementují rozhraní `ICollection(Of TInput)` (`ICollection<TInput>` v jazyce C#). To zajišťuje, že metodu <xref:System.Collections.Generic.ICollection%601.Add%2A> lze použít k přidání prvků.

    [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
    [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]

8. Definujte formální parametry metody pomocí metody <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A>. V tomto příkladu má metoda `Factory` jen jeden parametr, pole `TInput`. Tento typ je vytvořen zavoláním metody <xref:System.Type.MakeArrayType%2A> třídy <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, která představuje parametr `TInput`. Argument metody <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> je pole objektů <xref:System.Type>.

    [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
    [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]

9. Definujte návratový typ metody pomocí metody <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A>. V tomto příkladu je vrácena instance typu parametru `TOutput`.

    [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
    [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]

10. Vygenerujte tělo metody pomocí typu <xref:System.Reflection.Emit.ILGenerator>. Podrobnosti naleznete v souvisejícím postupu pro vygenerování těla metody.

    > [!IMPORTANT]
    > Při generování volání metod obecných typů v případě, že typy argumentů těchto typů jsou parametry typu obecné metody, je nutné pomocí přetížení metod `static`, <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29> a <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> deklarovaných jako <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> třídy <xref:System.Reflection.Emit.TypeBuilder> získat zkonstruované formy této metody. Tento fakt ukazuje související postup vygenerování těla metody.

11. Dokončete typ obsahující tuto metodu a sestavení uložte. Související postup volání obecné metody ukazuje dva způsoby volání dokončené metody.

    [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
    [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]

<a name="procedureSection1"></a>

### <a name="to-emit-the-method-body"></a>Vygenerování těla metody

1. Získejte generátor kódu a deklarujte místní proměnné a popisky. Metoda <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> se používá při deklarování lokálních proměnných. `ic` `TOutput` `retVal` `ICollection(Of TInput)` `ICollection<TInput>` `TOutput` C#Metoda má čtyři místní proměnné: pro uložení nového, který je vrácen metodou, pro uchování při přetypování do (v), `Factory` `input`pro uložení vstupního pole `TInput` objektů a `index` iterace v poli. Tato metoda má také dva popisky, jeden pro vstup do smyčky (`enterLoop`) a jeden pro začátek smyčky (`loopAgain`), definované pomocí metody <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A>.

    První věc, kterou metoda provede, je načtení jejího argumentu pomocí operačního kódu <xref:System.Reflection.Emit.OpCodes.Ldarg_0> a jeho uložení do místní proměnné `input` pomocí operačního kódu <xref:System.Reflection.Emit.OpCodes.Stloc_S>.

    [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
    [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]

2. Vygenerujte kód pro vytvoření instance objektu `TOutput` pomocí obecného přetížení metody <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>. Toto přetížení vyžaduje, aby zadaný typ měl konstruktor bez parametrů, což je důvodem pro přidání tohoto omezení parametru `TOutput`. Vytvořte konstruovanou obecnou metodu předáním parametru `TOutput` metodě <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Po vygenerování kódu pro volání této metody vygenerujte kód pro uložení do místní proměnné `retVal` pomocí operačního kódu <xref:System.Reflection.Emit.OpCodes.Stloc_S>

    [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
    [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]

3. Vygenerujte kód pro přetypování nového objektu `TOutput` na rozhraní `ICollection(Of TInput)` a uložte jej do místní proměnné `ic`.

    [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
    [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]

4. Získejte objekt <xref:System.Reflection.MethodInfo> představující metodu <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType>. Tato metoda pracuje s rozhraním `ICollection(Of TInput)` (`ICollection<TInput>` v jazyce C#), takže je nezbytné získat metodu `Add` specifickou pro konstruovaný typ. Nelze použít metodu <xref:System.Type.GetMethod%2A> pro získání objektu <xref:System.Reflection.MethodInfo> přímo z proměnné `icollOfTInput`, protože metoda <xref:System.Type.GetMethod%2A> není podporována typem, který byl zkonstruován pomocí typu <xref:System.Reflection.Emit.GenericTypeParameterBuilder>. Namísto toho zavolejte metodu <xref:System.Type.GetMethod%2A> proměnné `icoll`, která obsahuje definici obecného typu obecného rozhraní <xref:System.Collections.Generic.ICollection%601>. Poté použijte metodu <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> deklarovanou jako `static` pro vytvoření typu <xref:System.Reflection.MethodInfo> pro konstruovaný typ. Tento fakt ukazuje následující kód.

    [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
    [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]

5. Vygenerujte kód pro inicializaci proměnné `index` načtením 32bitového celého čísla 0 a uložte jej do proměnné. Vygenerujte kód větvení pro popisek `enterLoop`. Tento popisek dosud není označen, protože je uvnitř smyčky. Kód smyčky je vygenerován v dalším kroku.

    [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
    [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]

6. Vygenerujte kód smyčky. Prvním krokem je označit začátek smyčky voláním metody <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> s popiskem `loopAgain`. Příkazy větvení, které používají tento popisek, se budou nyní větvit do tohoto bodu kódu. Dalším krokem je vložení objektu `TOutput`, přetypovaného na rozhraní `ICollection(Of TInput)`, do zásobníku. To není nutné provádět okamžitě, ale objekt musí být vložen pro volání metody `Add`. Příště, když je vstupní pole vloženo do zásobníku, bude proměnná `index` obsahovat aktuální index pole. Operační kód <xref:System.Reflection.Emit.OpCodes.Ldelem> vyjme index a pole ze zásobníku a vloží indexovaný prvek pole do zásobníku. Zásobník je nyní připraven pro volání metody <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType>, která vyjme kolekci a nový prvek ze zásobníku a přidá prvek do kolekce.

    Zbytek kódu ve smyčce zvýší index a testy, aby bylo možné zjistit, zda je smyčka dokončena: Index a 32 celé číslo 1 jsou vloženy do zásobníku a přidány, přičemž součet v zásobníku zůstane. součet je uložen v `index`. Voláním metody <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> je tento bod nastaven jako vstupní bod smyčky. Index je znovu načten. Vstupní pole je vloženo do zásobníku a operační kód <xref:System.Reflection.Emit.OpCodes.Ldlen> je vygenerován pro získání jeho délky. Index a délka jsou nyní v zásobníku a operační kód <xref:System.Reflection.Emit.OpCodes.Clt> je vygenerován pro jejich porovnání. Pokud je index menší než délka, operační kód <xref:System.Reflection.Emit.OpCodes.Brtrue_S> provede větvení zpět na začátek smyčky.

    [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
    [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]

7. Vygenerujte kód pro vložení objektu `TOutput` do zásobníku a vrácení z metody. Místní proměnné `retVal` a `ic` obsahují odkazy na nový objekt `TOutput`. Proměnná `ic` se používá pouze pro přístup k metodě <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType>.

    [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
    [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]

<a name="procedureSection2"></a>

### <a name="to-invoke-the-generic-method"></a>Volání obecné metody

1. `Factory`je obecná definice metody. Aby ji bylo možné vyvolat, je nutné přiřadit typy parametrů obecného typu. To lze učinit použitím metody <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Následující kód vytvoří konstruovanou obecnou metodu, určí typ <xref:System.String> jako typ parametru `TInput` a typ `List(Of String)` (`List<string>` v jazyce C#) jako typ parametru `TOutput` a zobrazí řetězec představující tuto metodu.

    [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
    [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]

2. Chcete-li vyvolat metodu pomocí pozdní vazby, použijte metodu <xref:System.Reflection.MethodBase.Invoke%2A>. Následující kód vytvoří pole typů <xref:System.Object> obsahující jako jediný prvek pole řetězců a předá jej jako seznam argumentů obecné metodě. První parametr metody <xref:System.Reflection.MethodBase.Invoke%2A> je nulový odkaz, protože je tato metoda deklarovaná jako `static`. Vrácená hodnota je přetypována na typ `List(Of String)` a zobrazí se její první prvek.

    [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
    [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]

3. Chcete-li tuto metodu vyvolat pomocí delegáta, musíte mít delegáta, který odpovídá signatuře konstruované obecné metody. To lze snadno provést vytvořením obecného delegáta. Následující kód vytvoří instanci obecného delegáta `D` definovaného v příkladu kódu pomocí přetížení metody <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> a tohoto delegáta vyvolá. Delegáti poskytují vyšší výkon než volání s pozdní vazbou.

    [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
    [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]

4. Vygenerovanou metodu lze také volat z programu, který odkazuje na uložené sestavení.

## <a name="example"></a>Příklad

Následující příklad kódu vytvoří neobecný typ `DemoType` s obecnou metodou `Factory`. Tato metoda má dva parametry obecného typu, `TInput` určující vstupní typ a `TOutput` určující výstupní typ. Parametr typu `TOutput` je omezen na implementaci rozhraní `ICollection<TInput>` (`ICollection(Of TInput)` v jazyce Visual Basic), musí být odkazovým typem a mít konstruktor bez parametrů.

Tato metoda má jeden formální parametr, což je pole `TInput`. Metoda vrací instanci typu `TOutput`, která obsahuje všechny prvky vstupního pole. Parametr `TOutput` může být libovolný typ obecné kolekce, která implementuje obecné rozhraní <xref:System.Collections.Generic.ICollection%601>.

Při spuštění kódu je dynamické sestavení uloženo jako DemoGenericMethod1. dll a lze jej prozkoumat pomocí programu [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).

> [!NOTE]
> Vhodný způsob, jak se naučit generovat kód, je napsat program v jazyce Visual Basic, C# nebo Visual C++ provádějící úlohy, které chcete vygenerovat, a použít disassembler ke kontrole kódu produkovaného kompilátorem jazyka MSIL.

Příklad kódu obsahuje zdrojový kód, který je ekvivalentní s vygenerovanou metodou. Vygenerovaná metoda je zavolána s pozdní vazbou a také pomocí obecného delegáta deklarovaného v příkladu kódu.

[!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
[!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Emit.MethodBuilder>
- [Postupy: Definování obecného typu pomocí generování reflexe](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)
