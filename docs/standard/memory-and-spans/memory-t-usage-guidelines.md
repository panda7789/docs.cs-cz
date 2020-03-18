---
title: Pokyny k používání Memory<T> a Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121964"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Pokyny k používání Memory\<T> a Span\<T>

Jádro .NET obsahuje řadu typů, které představují libovolnou souvislou oblast paměti. .NET Core 2.0 <xref:System.Span%601> <xref:System.ReadOnlySpan%601>zavedena a , které jsou zjednodušené vyrovnávací paměti, které mohou být zálohovány spravované nebo nespravované paměti. Vzhledem k tomu, že tyto typy mohou být uloženy pouze v zásobníku, jsou nevhodné pro řadu scénářů, včetně volání asynchronní metody. .NET Core 2.1 přidává řadu dalších <xref:System.ReadOnlyMemory%601> <xref:System.Buffers.IMemoryOwner%601>typů, <xref:System.Buffers.MemoryPool%601>včetně <xref:System.Memory%601>, , a . Stejně jako <xref:System.Span%601>a <xref:System.Memory%601> jeho související typy mohou být zálohovány spravovanou i nespravovanou pamětí. Na <xref:System.Span%601> <xref:System.Memory%601> rozdíl od , mohou být uloženy na spravované haldy.

Obě <xref:System.Span%601> <xref:System.Memory%601> a jsou vyrovnávací paměti strukturovaných dat, které lze použít v kanálech. To znamená, že jsou navrženy tak, aby některá nebo všechna data mohla být efektivně předána součástem v kanálu, které je mohou zpracovat a volitelně upravit vyrovnávací paměť. Vzhledem k tomu, <xref:System.Memory%601> že a jeho související typy jsou přístupné více komponent nebo více vláken, je důležité, aby vývojáři dodržovat některé standardní pokyny pro použití k výrobě robustní kód.

## <a name="owners-consumers-and-lifetime-management"></a>Vlastníci, spotřebitelé a celoživotní správa

Vzhledem k tomu, že vyrovnávací paměti mohou být předány mezi rozhraními API a protože vyrovnávací paměti lze někdy přistupovat z více vláken, je důležité zvážit správu životnosti. Existují tři základní pojmy:

- **Vlastnictví**. Vlastník instance vyrovnávací paměti je zodpovědný za správu životnosti, včetně zničení vyrovnávací paměti, když se již nepoužívá. Všechny vyrovnávací paměti mají jednoho vlastníka. Obecně vlastník je součást, která vytvořila vyrovnávací paměť nebo která obdržela vyrovnávací paměť z továrny. Vlastnictví může být také převedeno; **Komponenta A** můžete vzdát řízení vyrovnávací paměti **komponenty B**, na kterém místě **Component-A** již nemusí používat vyrovnávací paměť a **Component-B** se stane zodpovědný za zničení vyrovnávací paměti, když je již používán.

- **Spotřeba**. Příjemce instance vyrovnávací paměti je povoleno použít instanci vyrovnávací paměti čtením z ní a případně zápis do něj. Vyrovnávací paměti mohou mít jednoho příjemce najednou, pokud není k dispozici nějaký mechanismus externí synchronizace. Všimněte si, že aktivní příjemce vyrovnávací paměti není nutně vlastníkem vyrovnávací paměti.

- **Pronájem**. Zapůjčení je doba, po kterou může být určitá součást příjemcem vyrovnávací paměti.

Následující příklad pseudokódu ilustruje tyto tři koncepty. Obsahuje metodu, `Main` která inkonaluje <xref:System.Memory%601> vyrovnávací paměť typu <xref:System.Char>, volá metodu `WriteInt32ToBuffer` pro zápis řetězcové `DisplayBufferToConsole` reprezentace celého čísla do vyrovnávací paměti a pak volá metodu k zobrazení hodnoty vyrovnávací paměti.

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

Metoda `Main` vytvoří vyrovnávací paměť (v <xref:System.Span%601> tomto případě instanci) a tak je jeho vlastníkem. Proto `Main` je zodpovědný za zničení vyrovnávací paměti, když již není používán. To provádí voláním <xref:System.Span%601.Clear?displayProperty=nameWithType> metody vyrovnávací paměti. (Metoda <xref:System.Span%601.Clear> zde ve skutečnosti vymaže <xref:System.Span%601> vyrovnávací paměti; struktura ve skutečnosti nemá metodu, která ničí vyrovnávací paměť.)

Vyrovnávací paměť má `WriteInt32ToBuffer` dva `DisplayBufferToConsole`spotřebitele a . Existuje pouze jeden spotřebitel najednou `WriteInt32ToBuffer`(první `DisplayBufferToConsole`, pak ) a ani jeden ze spotřebitelů vlastní vyrovnávací paměť. Všimněte si také, že "spotřebitel" v tomto kontextu neznamená zobrazení vyrovnávací paměti jen pro čtení; spotřebitelé můžete upravit obsah vyrovnávací `WriteInt32ToBuffer` paměti, stejně jako, pokud dané čtení a zápis zobrazení vyrovnávací paměti.

Metoda `WriteInt32ToBuffer` má zapůjčení (může spotřebovat) vyrovnávací paměť mezi začátkem volání metody a časem, kdy metoda vrátí. Podobně `DisplayBufferToConsole` má zapůjčení na vyrovnávací paměti při provádění a zapůjčení je uvolněna při uvolnění metody. (Neexistuje žádné rozhraní API pro správu zapůjčení; "zapůjčení" je koncepční záležitost.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Paměť\<T> a model vlastníka/spotřebitele

Jako [vlastníci, spotřebitelé a část správy životnosti](#owners-consumers-and-lifetime-management) poznámky, vyrovnávací paměť má vždy vlastníka. .NET Core podporuje dva modely vlastnictví:

- Model, který podporuje jedno vlastnictví. Vyrovnávací paměť má jednoho vlastníka po celou dobu jeho životnosti.

- Model, který podporuje převod vlastnictví. Vlastnictví vyrovnávací paměti lze převést z původního vlastníka (jeho tvůrce) do jiné součásti, která se pak stane zodpovědností za správu životnosti vyrovnávací paměti. Tento vlastník může zase převést vlastnictví na jinou součást a tak dále.

Rozhraní slouží <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> k explicitní správě vlastnictví vyrovnávací paměti. <xref:System.Buffers.IMemoryOwner%601>podporuje oba modely vlastnictví. Součást, která <xref:System.Buffers.IMemoryOwner%601> má odkaz vlastní vyrovnávací paměť. Následující příklad používá <xref:System.Buffers.IMemoryOwner%601?> instanci tak, <xref:System.Memory%601> aby odrážela vlastnictví vyrovnávací paměti.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Můžeme také napsat tento [`using`](../../csharp/language-reference/keywords/using-statement.md)příklad s :

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

V tomto kódu:

- Metoda `Main` obsahuje odkaz na <xref:System.Buffers.IMemoryOwner%601> instanci, takže `Main` metoda je vlastníkem vyrovnávací paměti.

- Metody `WriteInt32ToBuffer` `DisplayBufferToConsole` a <xref:System.Memory%601> přijmout jako veřejné rozhraní API. Proto jsou příjemci vyrovnávací paměti. A konzumují ho jen jednoho po druhém.

Přestože `WriteInt32ToBuffer` metoda je určena k zápisu `DisplayBufferToConsole` hodnoty do vyrovnávací paměti, metoda není. Aby to toto bylo možné, <xref:System.ReadOnlyMemory%601>mohla přijmout argument typu . Další informace <xref:System.ReadOnlyMemory%601>o tématu [naleznete v tématu rule #2: Use ReadOnlySpan\<T> nebo ReadOnlyMemory\<T> pokud by vyrovnávací paměť měla být jen pro čtení](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"Ownerless"\<Memory T> instance

Instanci <xref:System.Memory%601> můžete vytvořit <xref:System.Buffers.IMemoryOwner%601>bez použití aplikace . V tomto případě vlastnictví vyrovnávací paměti je implicitní spíše než explicitní a je podporován pouze model jednoho vlastníka. Můžete to udělat takto:

- Volání jednoho <xref:System.Memory%601> z konstruktorů přímo, `T[]`předávání v , jako následující příklad.

- Volání [string.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metoda rozšíření `ReadOnlyMemory<char>` k vytvoření instance.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metoda, která zpočátku vytvoří <xref:System.Memory%601> instanci je implicitní vlastník vyrovnávací paměti. Vlastnictví nelze převést na jinou součást, protože neexistuje žádná <xref:System.Buffers.IMemoryOwner%601> instance, která by převod usnadnila. (Jako alternativu si můžete také představit, že uvolňování času runtime vlastní vyrovnávací paměť a všechny metody právě spotřebovávají vyrovnávací paměť.)

## <a name="usage-guidelines"></a>Pokyny k použití

Vzhledem k tomu, že blok paměti je vlastněn, ale má být předán více součástem, z nichž některé <xref:System.Memory%601> <xref:System.Span%601>mohou pracovat na určitém bloku paměti současně, je důležité stanovit pokyny pro použití obou a .  Pokyny jsou nezbytné, protože:

- Je možné, že součást zachovat odkaz na blok paměti po jeho vlastník a vydal.

- Je možné, že součást pracovat na vyrovnávací paměti ve stejnou dobu, že jiná součást pracuje na něm, v procesu poškození dat ve vyrovnávací paměti.

- Zatímco charakter přidělené zásobníku <xref:System.Span%601> optimalizuje <xref:System.Span%601> výkon a umožňuje upřednostňovaný typ pro <xref:System.Span%601> provoz na bloku paměti, také podrobí některé hlavní omezení. Je důležité vědět, kdy <xref:System.Span%601> a a <xref:System.Memory%601>kdy použít .

Níže jsou uvedeny naše <xref:System.Memory%601> doporučení pro úspěšné použití a související typy. Všimněte si, že <xref:System.Memory%601> <xref:System.Span%601> pokyny, které <xref:System.ReadOnlyMemory%601> <xref:System.ReadOnlySpan%601> se vztahují a také se vztahuje na a pokud jsme výslovně na vědomí jinak.

**Pravidlo #1: Pro synchronní rozhraní API\<použijte span\<t> místo paměti T> jako parametr, pokud je to možné.**

<xref:System.Span%601>je univerzálnější než <xref:System.Memory%601> a může představovat širší škálu souvislých vyrovnávacích pamětí paměti. <xref:System.Span%601>nabízí také lepší <xref:System.Memory%601>výkon než . Nakonec můžete <xref:System.Memory%601.Span?displayProperty=nameWithType> vlastnost převést <xref:System.Memory%601> instanci <xref:System.Span%601>na ,\<i když Span\<T>-to-Memory T> převod není možný. Takže pokud vaši volající náhodou <xref:System.Memory%601> mají instanci, budou moci <xref:System.Span%601> volat vaše metody s parametry stejně.

Použití parametru <xref:System.Span%601> typu namísto typu <xref:System.Memory%601> také pomáhá napsat správnou implementaci metody spotřeby. Budete automaticky získat kontroly v době kompilace, abyste zajistili, že se nepokoušíte o přístup k vyrovnávací paměti nad rámec zapůjčení metody (více o tom později).

Někdy budete muset použít <xref:System.Memory%601> parametr namísto <xref:System.Span%601> parametru, i když jste plně synchronní. Rozhraní API, které jste <xref:System.Memory%601> závislí přijímá pouze argumenty. To je v pořádku, ale být vědomi <xref:System.Memory%601> kompromisy zapojeny při použití synchronně.

<a name="rule-2" />

**Pravidlo #2: Použijte ReadOnlySpan\<T\<> nebo ReadOnlyMemory T> pokud vyrovnávací paměť by měla být jen pro čtení.**

V předchozích příkladech `DisplayBufferToConsole` metoda čte pouze z vyrovnávací paměti; nemění obsah vyrovnávací paměti. Podpis metody by měl být změněn na následující.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

Ve skutečnosti, pokud zkombinujeme toto pravidlo a pravidlo #1, můžeme udělat ještě lépe a přepsat podpis metody takto:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

Metoda `DisplayBufferToConsole` nyní pracuje prakticky s každým typu `T[]`vyrovnávací paměti, který si lze představit: , úložiště přidělené [s stackalloc](../../csharp/language-reference/operators/stackalloc.md)a tak dále. Můžete dokonce předat <xref:System.String> přímo do něj!

**Pravidlo #3: Pokud vaše\<metoda přijme `void`memory t> a\<vrátí , nesmíte použít Memory T> instance po vrátí metodu.**

To se týká již zmíněného "nájemního" konceptu. Zapůjčení metody vrácení prázdnoty na <xref:System.Memory%601> instanci začíná, když je metoda zadána, a končí při ukončení metody. Zvažte následující příklad, `Log` který volá ve smyčce na základě vstupu z konzoly.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Pokud `Log` je plně synchronní metoda, tento kód se bude chovat podle očekávání, protože je pouze jeden aktivní příjemce instance paměti v daném okamžiku.
Ale představte `Log` si, že místo toho, že má tuto realizaci.

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

V této `Log` implementaci porušuje jeho zapůjčení, protože <xref:System.Memory%601> se stále pokouší použít instanci na pozadí po původní metoda byla vrácena. Metoda `Main` může zmutovat `Log` vyrovnávací paměti při pokusech o čtení z ní, což může mít za následek poškození dat.

Existuje několik způsobů, jak tento problém vyřešit:

- Metoda `Log` může vrátit <xref:System.Threading.Tasks.Task> místo `void`, jako následující `Log` implementace metody.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log`místo toho mohou být implementovány takto:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Pravidlo #4: Pokud vaše metoda\<přijímá paměť T> a vrátí\<Task, nesmíte použít memory t> instance po Task přechody do terminálového stavu.**

Toto je pouze asynchronní varianta pravidla #3. Metoda `Log` z předchozího příkladu může být zapsána takto, aby byla v souladu s tímto pravidlem:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Zde "terminálový stav" znamená, že úloha přechází do dokončeného, chybově nebo zrušeného stavu. Jinými slovy, "terminálový stav" znamená "vše, co by způsobilo čekání na vyvolání nebo pokračování v provádění".

Tyto pokyny platí pro <xref:System.Threading.Tasks.Task>metody, které vracejí , <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>nebo podobný typ.

**Pravidlo #5: Pokud konstruktor\<přijímá paměť T> jako parametr, instance metody na konstruované\<objektu jsou považovány za spotřebitele memory t> instance.**

Uvažujte následující příklad:

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

Zde `OddValueExtractor` konstruktor přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže samotný konstruktor je `ReadOnlyMemory<int>` příjemcem instance a všechny metody instance na `ReadOnlyMemory<int>` vrácené hodnotě jsou také příjemci původní instance. To znamená, `TryReadNextOddValue` že `ReadOnlyMemory<int>` spotřebovává instanci, i když instance `TryReadNextOddValue` není předána přímo metodě.

**Pravidlo #6: Pokud máte nastavenou paměť\<T> typem vlastnosti (nebo ekvivalentní instance metody) na váš typ,\<instance metody na tento objekt se předpokládá, že jsou příjemci memory t> instance.**

To je opravdu jen varianta pravidla #5. Toto pravidlo existuje, protože settery vlastností nebo ekvivalentní metody se předpokládá, že zachytit a zachovat jejich vstupy, takže instance metody na stejný objekt může využít zachyceného stavu.

Následující příklad aktivuje toto pravidlo:

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

**Pravidlo #7: Pokud máte Odkaz\<na IMemoryOwner T>, musíte jej v určitém okamžiku nakládat nebo převést jeho vlastnictví (ale ne obojí).**

Vzhledem <xref:System.Memory%601> k tomu, že instance může být zálohována <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> spravovanou <xref:System.Memory%601> nebo nespravovanou pamětí, vlastník musí volat po dokončení práce provedené na instanci. Případně vlastník může převést vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou součást, v tomto okamžiku <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> se nabývající komponenta stane odpovědnou za volání ve vhodnou dobu (více o tom později).

Selhání volání <xref:System.Buffers.MemoryPool%601.Dispose%2A> metody může vést k nevracení nespravované paměti nebo jiné snížení výkonu.

Toto pravidlo platí také pro kód, který volá metody factory jako <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>. Volající se stane vlastníkem <xref:System.Buffers.IMemoryOwner%601> vrácené a je zodpovědný za likvidaci instance po dokončení.

**Pravidlo #8: Pokud máte v\<povrchu rozhraní API parametr IMemoryOwner T>, přijímáte vlastnictví této instance.**

Přijetí instance tohoto typu signalizuje, že vaše komponenta má v úmyslu převzít vlastnictví této instance. Vaše součást k tomu se stává zodpovědní za správnou likvidaci podle pravidla #7.

Jakákoli součást, která <xref:System.Buffers.IMemoryOwner%601> převádí vlastnictví instance na jinou součást, by již neměla tuto instanci používat po dokončení volání metody.

> [!IMPORTANT]
> Pokud konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho <xref:System.IDisposable>typ by <xref:System.IDisposable.Dispose%2A> měl <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>implementovat a vaše metoda by měla volat .

**Pravidlo #9: Pokud balíte synchronní metodu p/invoke, vaše\<rozhraní API by mělo jako parametr přijmout> Span T.**

Podle pravidla #1 <xref:System.Span%601> je obecně správný typ pro synchronní api. Instance můžete <xref:System.Span%601> připnout pomocí klíčového [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) slova, jako v následujícím příkladu.

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

V předchozím příkladu `pbData` může být null, pokud je například vstupní rozsah prázdný. Pokud exportovaná metoda absolutně `pbData` vyžaduje, aby byla `cbData` nenulová, i když je 0, může být metoda implementována následovně:

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

**Pravidlo #10: Pokud balíte asynchronní metodu p/invoke,\<vaše rozhraní API by mělo jako parametr přijmout paměť T>.**

Vzhledem k [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) tomu, že nelze použít klíčové <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> slovo napříč asynchronními operacemi, použijete metodu k připnutí <xref:System.Memory%601> instancí bez ohledu na druh souvislé paměti, kterou instance představuje. Následující příklad ukazuje, jak používat toto rozhraní API k provedení asynchronního volání p/invoke.

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)state;
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a>Viz také

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
