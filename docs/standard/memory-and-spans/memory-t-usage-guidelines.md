---
title: Pokyny k používání Memory<T> a Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121964"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>\<v paměti > a rozpětí\<T > pokyny pro použití

.NET Core obsahuje několik typů, které reprezentují libovolnou souvislou oblast paměti. Rozhraní .NET Core 2,0 zavedlo <xref:System.Span%601> a <xref:System.ReadOnlySpan%601>, což jsou odlehčené vyrovnávací paměti, které mohou být zajištěny spravovanou nebo nespravovanou pamětí. Vzhledem k tomu, že tyto typy mohou být uloženy pouze v zásobníku, nejsou vhodné pro různé scénáře, včetně volání asynchronní metody. .NET Core 2,1 přidává mnoho dalších typů, včetně <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>a <xref:System.Buffers.MemoryPool%601>. Stejně jako <xref:System.Span%601>, <xref:System.Memory%601> a jeho související typy lze zálohovat pomocí spravované i nespravované paměti. Na rozdíl od <xref:System.Span%601>mohou být <xref:System.Memory%601> uloženy na spravované haldě.

<xref:System.Span%601> i <xref:System.Memory%601> jsou vyrovnávací paměti strukturovaných dat, která se dají používat v kanálech. To znamená, že jsou navržené tak, aby některá nebo všechna data mohla být efektivně předána součástem v kanálu, která je může zpracovávat a případně upravovat vyrovnávací paměť. Vzhledem k tomu, že <xref:System.Memory%601> a ke svým souvisejícím typům lze získat pøístup více komponent nebo více vlákny, je důležité, aby vývojáři při vytváření robustního kódu dodržovali některé standardní pokyny pro použití.

## <a name="owners-consumers-and-lifetime-management"></a>Vlastníci, spotřebitelé a správa životního cyklu

Vzhledem k tomu, že vyrovnávací paměti lze předávat mezi rozhraními API a vzhledem k tomu, že vyrovnávací paměti mohou být někdy k dispozici z více vláken, je důležité zvážit správu životnosti. Existují tři základní koncepty:

- **Vlastnictví**. Vlastník instance vyrovnávací paměti je zodpovědný za správu životnosti, včetně zničení vyrovnávací paměti, když se už nepoužívá. Všechny vyrovnávací paměti mají jednoho vlastníka. Obecně je vlastníkem komponenta, která vytvořila vyrovnávací paměť nebo která obdržela vyrovnávací paměť z továrny. Vlastnictví lze také přenést; **Součást-a** může opustit řízení vyrovnávací paměti pro **komponentu B**, na které **Komponenta bodu-A** již nesmí používat vyrovnávací paměť, a **Komponenta B** se stane zodpovědností za zničení vyrovnávací paměti, pokud se už nepoužívá.

- **Spotřeba**. Příjemce instance vyrovnávací paměti může použít instanci vyrovnávací paměti čtením z ní a případně do ní zapisovat. Vyrovnávací paměti můžou mít jednoho příjemce v čase, pokud není k dispozici nějaký mechanismus externí synchronizace. Všimněte si, že aktivní příjemce vyrovnávací paměti nemusí být nutně vlastníkem vyrovnávací paměti.

- **Zapůjčení**. Zapůjčení je doba, po kterou může určitá součást být příjemcem vyrovnávací paměti.

Následující příklad pseudo kódu znázorňuje tyto tři koncepty. Obsahuje `Main` metodu, která vytvoří instanci <xref:System.Memory%601> vyrovnávací paměti typu <xref:System.Char>, volá metodu `WriteInt32ToBuffer` pro zápis řetězcové reprezentace celého čísla do vyrovnávací paměti a potom zavolá metodu `DisplayBufferToConsole` pro zobrazení hodnoty vyrovnávací paměti.

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

Metoda `Main` vytvoří vyrovnávací paměť (v tomto případě instance <xref:System.Span%601>) a tedy její vlastníka. Proto `Main` zodpovídá za zničení vyrovnávací paměti, když se už nepoužívá. Provede to voláním metody <xref:System.Span%601.Clear?displayProperty=nameWithType> vyrovnávací paměti. (<xref:System.Span%601.Clear> metoda ve skutečnosti vymaže paměť vyrovnávací paměti; struktura <xref:System.Span%601> ve skutečnosti nemá metodu, která zničí vyrovnávací paměť.)

Vyrovnávací paměť má dva uživatele `WriteInt32ToBuffer` a `DisplayBufferToConsole`. V jednom okamžiku je jen jeden příjemce (první `WriteInt32ToBuffer`, potom `DisplayBufferToConsole`) a žádný z uživatelů nevlastní vyrovnávací paměť. Všimněte si také, že "příjemce" v tomto kontextu neznamená zobrazení vyrovnávací paměti jen pro čtení. Uživatelé můžou upravit obsah vyrovnávací paměti, jak `WriteInt32ToBuffer` v případě, že je pro čtení a zápis vyrovnávací paměti.

Metoda `WriteInt32ToBuffer` má zapůjčení (může spotřebovávat) vyrovnávací paměť mezi začátkem volání metody a časem, který metoda vrátí. Podobně `DisplayBufferToConsole` má zapůjčení ve vyrovnávací paměti během jeho provádění a zapůjčení je uvolněno, pokud metoda odvíjí. (K dispozici není žádné rozhraní API pro správu zapůjčených adres. "zapůjčení" je koncepční záležitost.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Paměť\<> a model vlastník/příjemce

Jako poznámky k oddílům [pro vlastníky, uživatele a správu životního cyklu](#owners-consumers-and-lifetime-management) má vyrovnávací paměť vždy vlastníka. .NET Core podporuje dva modely vlastnictví:

- Model, který podporuje jediné vlastnictví. Vyrovnávací paměť má jednoho vlastníka pro celou dobu života.

- Model, který podporuje přenos vlastnictví. Vlastnictví vyrovnávací paměti lze přenést od původního vlastníka (jeho tvůrce) do jiné součásti, která pak bude zodpovědná za správu životnosti vyrovnávací paměti. Vlastník může převést vlastnictví na jinou komponentu a tak dále.

Rozhraní <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> použijete k explicitní správě vlastnictví vyrovnávací paměti. <xref:System.Buffers.IMemoryOwner%601> podporuje oba modely vlastnictví. Komponenta, která má odkaz <xref:System.Buffers.IMemoryOwner%601> vlastní vyrovnávací paměť. Následující příklad používá instanci <xref:System.Buffers.IMemoryOwner%601?> pro reflektování vlastnictví <xref:System.Memory%601> vyrovnávací paměti.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Tento příklad můžeme také zapsat s [`using`](../../csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

V tomto kódu:

- Metoda `Main` obsahuje odkaz na instanci <xref:System.Buffers.IMemoryOwner%601>, takže metoda `Main` je vlastníkem vyrovnávací paměti.

- Metody `WriteInt32ToBuffer` a `DisplayBufferToConsole` přijímají <xref:System.Memory%601> jako veřejné rozhraní API. Proto jsou příjemci vyrovnávací paměti. A využívají je pouze po jednom.

I když je metoda `WriteInt32ToBuffer` určena k zápisu hodnoty do vyrovnávací paměti, metoda `DisplayBufferToConsole` není. V takovém případě by bylo možné akceptovat argument typu <xref:System.ReadOnlyMemory%601>. Další informace o <xref:System.ReadOnlyMemory%601>najdete v tématu [pravidla #2: použijte ReadOnlySpan\<t > nebo ReadOnlyMemory\<t >, pokud by měla být vyrovnávací paměť jen pro čtení](#rule-2).

### <a name="ownerless-memoryt-instances"></a>Nevlastní > instance\<paměti pro vlastníka

Instanci <xref:System.Memory%601> můžete vytvořit bez použití <xref:System.Buffers.IMemoryOwner%601>. V takovém případě je vlastnictví vyrovnávací paměti implicitní, nikoli explicitní, a podporuje se jenom model s jedním vlastníkem. Můžete to udělat takto:

- Volání jednoho konstruktoru <xref:System.Memory%601> přímo, předání do `T[]`, jak je uvedeno v následujícím příkladu.

- Voláním metody rozšíření [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) vytvořte instanci `ReadOnlyMemory<char>`.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metoda, která zpočátku vytvoří instanci <xref:System.Memory%601>, je implicitní vlastník vyrovnávací paměti. Vlastnictví nelze přenést do žádné jiné součásti, protože není k dispozici žádná instance <xref:System.Buffers.IMemoryOwner%601> pro usnadnění přenosu. (Jako alternativu můžete také představovat, že systém uvolňování paměti modulu runtime vlastní vyrovnávací paměť, a všechny metody pouze využívají vyrovnávací paměť.)

## <a name="usage-guidelines"></a>Pokyny k použití

Vzhledem k tomu, že blok paměti je vlastněn, ale má být předán více komponentám, některé z nich mohou fungovat současně na konkrétní blok paměti, je důležité vytvořit pokyny pro použití <xref:System.Memory%601> i <xref:System.Span%601>.  Pokyny jsou nezbytné z těchto důvodů:

- Je možné, že komponenta uchovává odkaz na blok paměti poté, co ho jeho vlastník uvolnil.

- Je možné, že komponenta pracuje na vyrovnávací paměti současně s tím, že na ní jiná komponenta pracuje, v procesu poškození dat ve vyrovnávací paměti.

- I když povaha přidělená do zásobníku <xref:System.Span%601> optimalizuje výkon a dává <xref:System.Span%601> upřednostňovaný typ pro provoz na bloku paměti, také subjekty <xref:System.Span%601> na některá hlavní omezení. Je důležité znát, kdy použít <xref:System.Span%601> a kdy použít <xref:System.Memory%601>.

Níže jsou naše doporučení pro úspěšné použití <xref:System.Memory%601> a souvisejících typů. Všimněte si, že pokyny, které se vztahují na <xref:System.Memory%601> a <xref:System.Span%601>, platí i pro <xref:System.ReadOnlyMemory%601> a <xref:System.ReadOnlySpan%601>, pokud výslovně nepovažujeme za jinak.

**#1 pravidla: u synchronního rozhraní API použijte >\<T místo paměti\<T > jako parametr, pokud je to možné.**

<xref:System.Span%601> je všestrannější než <xref:System.Memory%601> a může představovat širší škálu souvislých vyrovnávacích pamětí. <xref:System.Span%601> také nabízí lepší výkon než <xref:System.Memory%601>. Nakonec můžete použít vlastnost <xref:System.Memory%601.Span?displayProperty=nameWithType> k převedení instance <xref:System.Memory%601> na <xref:System.Span%601>, i když je\<T > převod na paměť\<T > převod není možný. Takže v případě, že se volající mají instanci <xref:System.Memory%601>, budou moci volat vaše metody s parametry <xref:System.Span%601> přesto.

Použití parametru typu <xref:System.Span%601> místo typu <xref:System.Memory%601> také pomůže napsat správnou implementaci metody. Automaticky získáte kontroly za běhu, abyste se ujistili, že se nepokoušíte o přístup k vyrovnávací paměti nad zapůjčením vaší metody (Další informace najdete později).

V některých případech budete muset místo parametru <xref:System.Span%601> použít parametr <xref:System.Memory%601>, a to i v případě, že jste plně synchronně. Možná rozhraní API, které závisí, přijímá pouze <xref:System.Memory%601> argumentů. Je to v pořádku, ale mějte na paměti, že při použití <xref:System.Memory%601> synchronně se jedná o kompromisy.

<a name="rule-2" />

**#2 pravidla: použijte ReadOnlySpan\<T > nebo ReadOnlyMemory\<T >, pokud by měla být vyrovnávací paměť jen pro čtení.**

V předchozích příkladech metoda `DisplayBufferToConsole` čte pouze z vyrovnávací paměti; neupravuje obsah vyrovnávací paměti. Signatura metody by se měla změnit na následující.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

V případě, že toto pravidlo a pravidlo kombinujeme #1, můžeme ještě lepší a přepsat signaturu metody následujícím způsobem:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

Metoda `DisplayBufferToConsole` nyní funguje s prakticky všemi typy vyrovnávací paměti, které lze předcházet: `T[]`, úložiště přidělené [stackalloc](../../csharp/language-reference/operators/stackalloc.md)a tak dále. Můžete dokonce předat <xref:System.String> přímo na to!

**#3 pravidla: Pokud vaše metoda přijímá paměť\<T > a vrátí `void`, nemusíte po návratu metody použít instanci paměti\<T >.**

To se týká konceptu zapůjčení uvedeného výše. Zapůjčení metody vracející hodnotu void u <xref:System.Memory%601> instance začíná při zadání metody a končí při ukončení metody. Vezměte v úvahu následující příklad, který volá `Log` ve smyčce na základě vstupu z konzoly.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Pokud je `Log` plně synchronní metodou, bude tento kód fungovat podle očekávání, protože v daném okamžiku existuje pouze jeden aktivní spotřebitel instance paměti.
Ale představte si, že `Log` má tuto implementaci.

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

V této implementaci `Log` porušuje své zapůjčení, protože se stále pokouší použít instanci <xref:System.Memory%601> na pozadí po vrácení původní metody. Metoda `Main` by mohla způsobit vyrovnávací paměť, zatímco `Log` se z ní pokusí číst, což by mohlo vést k poškození dat.

Tuto chybu lze vyřešit několika způsoby:

- Metoda `Log` může vracet <xref:System.Threading.Tasks.Task> namísto `void`, jako následující implementace metody `Log`.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- místo toho `Log` možné implementovat následujícím způsobem:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**#4 pravidla: Pokud vaše metoda přijímá paměť\<T > a vrátí úlohu, po přechodu úlohy do stavu terminálu nemusíte používat instanci paměti\<T >.**

Toto je pouze asynchronní varianta pravidla #3. Metodu `Log` z předchozího příkladu můžete zapsat takto, aby splňovala toto pravidlo:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

V tomto případě "stav terminálu" znamená, že se úloha přechází do stavu dokončeno, chyba nebo zrušeno. Jinými slovy "Terminal State" znamená "cokoli, co by způsobilo, že se očekává, že se má vyvolávat nebo pokračovat v provádění."

Tento návod se vztahuje na metody, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>nebo jakýkoli podobný typ.

**#5 pravidla: Pokud váš konstruktor přijímá paměť\<T > jako parametr, předpokládá se, že metody instance na vytvořeném objektu budou spotřebiteli instance paměti\<T >.**

Vezměte v úvahu následující příklad:

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

V tomto případě konstruktor `OddValueExtractor` přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže samotný konstruktor je příjemcem instance `ReadOnlyMemory<int>` a všechny metody instance vrácené hodnoty jsou také příjemci původní instance `ReadOnlyMemory<int>`. To znamená, že `TryReadNextOddValue` spotřebovává `ReadOnlyMemory<int>` instanci, i když instance není předána přímo metodě `TryReadNextOddValue`.

**#6 pravidla: Pokud máte ve svém typu nastavitelnou vlastnost\<T >-Type (nebo ekvivalentní metodu instance), předpokládá se, že metody instance tohoto objektu budou spotřebiteli instance paměti\<T >.**

Toto je opravdu pouze varianta pravidla #5. Toto pravidlo existuje, protože metody setter nebo ekvivalentní metody jsou považovány za zachycení a uchování jejich vstupů, takže metody instance u stejného objektu mohou využívat zachycený stav.

Toto pravidlo se spustí v následujícím příkladu:

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

**#7 pravidla: Pokud máte > odkazem na\<IMemoryOwner, je potřeba, abyste ho odstranili nebo přenesli jeho vlastnictví (ale ne obojí).**

Vzhledem k tomu, že instance <xref:System.Memory%601> může být zajištěna buď spravovanou, nebo nespravovanou pamětí, musí vlastník volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>, pokud je dokončená práce na instanci <xref:System.Memory%601>. Alternativně může vlastník přenést vlastnictví instance <xref:System.Buffers.IMemoryOwner%601> do jiné komponenty. v takovém případě se komponenta pro získání bude zodpovědná za volání <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> v příslušné době (Další informace najdete později).

Selhání volání metody <xref:System.Buffers.MemoryPool%601.Dispose%2A> může vést k nevrácení nespravované paměti nebo jinému snížení výkonu.

Toto pravidlo platí také pro kód, který volá metody objektu pro vytváření, jako je <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>. Volající se stane vlastníkem vráceného <xref:System.Buffers.IMemoryOwner%601> a zodpovídá za likvidaci instance po dokončení.

**#8 pravidla: Pokud máte na ploše rozhraní API parametr IMemoryOwner\<T >, přijímáte vlastnictví této instance.**

Přijetí instance tohoto typu signalizuje, že vaše komponenta zamýšlí převzít vlastnictví této instance. Vaše komponenta se bude zodpovědná za řádné vyřazení podle pravidla #7.

Jakákoli komponenta, která přenáší vlastnictví instance <xref:System.Buffers.IMemoryOwner%601> na jinou komponentu, by již neměla používat tuto instanci po dokončení volání metody.

> [!IMPORTANT]
> Pokud konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho typ by měl implementovat <xref:System.IDisposable>a metoda <xref:System.IDisposable.Dispose%2A> by měla volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.

**#9 pravidla: Pokud zabalíte synchronní metodu volání nespravovaného volání, rozhraní API by mělo jako parametr přijmout\<T >.**

V souladu s pravidly #1 je <xref:System.Span%601> správného typu, který se má použít pro synchronní rozhraní API. Instance <xref:System.Span%601> můžete připnout pomocí klíčového slova [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) , jak je uvedeno v následujícím příkladu.

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

V předchozím příkladu může `pbData` mít hodnotu null, pokud je například vstupní rozpětí prázdné. Pokud exportovaná metoda naprosto vyžaduje, aby `pbData` být nenulové, i když je `cbData` 0, může být metoda implementována takto:

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

**#10 pravidla: Pokud zabalíte asynchronní metodu volání nespravovaného volání, rozhraní API by mělo jako parametr přijímat paměť\<T >.**

Vzhledem k tomu, že nemůžete použít klíčové slovo [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) napříč asynchronními operacemi, použijte metodu <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> k připnutí instancí <xref:System.Memory%601>, bez ohledu na druh souvislé paměti, kterou instance představuje. Následující příklad ukazuje, jak použít toto rozhraní API k provedení asynchronního volání volání nespravovaného volání.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
