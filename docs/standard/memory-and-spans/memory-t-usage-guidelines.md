---
title: Pokyny k používání Memory<T> a Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: b89969f212da6ac90d0fb0d1bf388626e136b92e
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158590"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Pokyny k používání Memory\<T> a Span\<T>

.NET Core obsahuje několik typů, které reprezentují libovolnou souvislou oblast paměti. .NET Core 2,0 zavádí <xref:System.Span%601> a <xref:System.ReadOnlySpan%601>, což jsou odlehčené vyrovnávací paměti, které mohou být zajištěny spravovanou nebo nespravovanou pamětí. Vzhledem k tomu, že tyto typy mohou být uloženy pouze v zásobníku, nejsou vhodné pro různé scénáře, včetně volání asynchronní metody. .NET Core 2,1 přidává mnoho dalších typů, <xref:System.Memory%601>včetně, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>a. <xref:System.Buffers.MemoryPool%601> Podobně <xref:System.Span%601>jako <xref:System.Memory%601> a jeho související typy lze zálohovat pomocí spravované i nespravované paměti. Na rozdíl <xref:System.Span%601>od <xref:System.Memory%601> , může být uloženo na spravované haldě.

Obojí <xref:System.Span%601> i <xref:System.Memory%601> jsou vyrovnávací paměti strukturovaných dat, která lze použít v kanálech. To znamená, že jsou navržené tak, aby některá nebo všechna data mohla být efektivně předána součástem v kanálu, která je může zpracovávat a případně upravovat vyrovnávací paměť. Vzhledem <xref:System.Memory%601> k tomu, že a ke kterým souvisejícímu typu lze získat pøístup více komponent nebo více vlákny, je důležité, aby vývojáři při vytváření robustního kódu dodržovali některé standardní pokyny pro použití.

## <a name="owners-consumers-and-lifetime-management"></a>Vlastníci, spotřebitelé a správa životního cyklu

Vzhledem k tomu, že vyrovnávací paměti lze předávat mezi rozhraními API a vzhledem k tomu, že vyrovnávací paměti mohou být někdy k dispozici z více vláken, je důležité zvážit správu životnosti. Existují tři základní koncepty:

- **Vlastnictví**. Vlastník instance vyrovnávací paměti je zodpovědný za správu životnosti, včetně zničení vyrovnávací paměti, když se už nepoužívá. Všechny vyrovnávací paměti mají jednoho vlastníka. Obecně je vlastníkem komponenta, která vytvořila vyrovnávací paměť nebo která obdržela vyrovnávací paměť z továrny. Vlastnictví lze také přenést; **Součást-a** může opustit řízení vyrovnávací paměti pro **komponentu B**, na které **Komponenta bodu-A** již nesmí používat vyrovnávací paměť, a **Komponenta B** se stane zodpovědností za zničení vyrovnávací paměti, pokud se už nepoužívá.

- **Spotřeba**. Příjemce instance vyrovnávací paměti může použít instanci vyrovnávací paměti čtením z ní a případně do ní zapisovat. Vyrovnávací paměti můžou mít jednoho příjemce v čase, pokud není k dispozici nějaký mechanismus externí synchronizace. Aktivní příjemce vyrovnávací paměti nemusí být nutně vlastníkem vyrovnávací paměti.

- **Zapůjčení**. Zapůjčení je doba, po kterou může určitá součást být příjemcem vyrovnávací paměti.

Následující příklad pseudo kódu znázorňuje tyto tři koncepty. `Main` Obsahuje metodu <xref:System.Memory%601> , která vytváří instanci vyrovnávací paměti typu <xref:System.Char>, volá `WriteInt32ToBuffer` metodu pro zápis řetězcové reprezentace celého čísla do vyrovnávací paměti a poté volá `DisplayBufferToConsole` metodu pro zobrazení hodnoty vyrovnávací paměti.

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

`Main` Metoda vytvoří vyrovnávací paměť (v tomto případě <xref:System.Span%601> instance) a tedy její vlastníka. Proto zodpovídá `Main` za zničení vyrovnávací paměti, když se už nepoužívá. Provede to voláním <xref:System.Span%601.Clear?displayProperty=nameWithType> metody vyrovnávací paměti. (Tato <xref:System.Span%601.Clear> metoda ve skutečnosti vymaže paměť vyrovnávací paměti; <xref:System.Span%601> struktura ve skutečnosti nemá metodu, která zničí vyrovnávací paměť.)

Vyrovnávací paměť má dva uživatele `WriteInt32ToBuffer` a. `DisplayBufferToConsole` V jednom okamžiku je k dispozici pouze jeden příjemce `WriteInt32ToBuffer`(první `DisplayBufferToConsole`, potom) a žádný z uživatelů vlastní vyrovnávací paměť. Všimněte si také, že "příjemce" v tomto kontextu neznamená zobrazení vyrovnávací paměti jen pro čtení. Uživatelé můžou upravovat obsah vyrovnávací paměti, jak `WriteInt32ToBuffer` to dělá, pokud je k dispozici zobrazení pro čtení a zápis vyrovnávací paměti.

`WriteInt32ToBuffer` Metoda má zapůjčení (může spotřebovat) vyrovnávací paměť mezi začátkem volání metody a časem, který metoda vrátí. Podobně `DisplayBufferToConsole` má zapůjčení ve vyrovnávací paměti během jeho provádění a zapůjčení je uvolněno při zrušení metody. (K dispozici není žádné rozhraní API pro správu zapůjčených adres. "zapůjčení" je koncepční záležitost.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>>\<paměti a model vlastník/příjemce

Jako poznámky k oddílům [pro vlastníky, uživatele a správu životního cyklu](#owners-consumers-and-lifetime-management) má vyrovnávací paměť vždy vlastníka. .NET Core podporuje dva modely vlastnictví:

- Model, který podporuje jediné vlastnictví. Vyrovnávací paměť má jednoho vlastníka pro celou dobu života.

- Model, který podporuje přenos vlastnictví. Vlastnictví vyrovnávací paměti lze přenést od původního vlastníka (jeho tvůrce) do jiné součásti, která pak bude zodpovědná za správu životnosti vyrovnávací paměti. Vlastník může převést vlastnictví na jinou komponentu a tak dále.

<xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> Rozhraní použijete k explicitní správě vlastnictví vyrovnávací paměti. <xref:System.Buffers.IMemoryOwner%601>podporuje oba modely vlastnictví. Komponenta, která má <xref:System.Buffers.IMemoryOwner%601> odkaz na vlastní vyrovnávací paměť. Následující příklad používá <xref:System.Buffers.IMemoryOwner%601?> instanci pro reflektování vlastnictví <xref:System.Memory%601> vyrovnávací paměti.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Tento příklad můžeme také zapsat pomocí [`using`](../../csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

V tomto kódu:

- `Main` Metoda obsahuje odkaz na <xref:System.Buffers.IMemoryOwner%601> instanci, takže `Main` metoda je vlastníkem vyrovnávací paměti.

- Metody `WriteInt32ToBuffer` a `DisplayBufferToConsole` AKCEPTUJÍ <xref:System.Memory%601> jako veřejné rozhraní API. Proto jsou příjemci vyrovnávací paměti. A využívají je pouze po jednom.

I když `WriteInt32ToBuffer` je metoda určena pro zápis hodnoty do vyrovnávací paměti, `DisplayBufferToConsole` metoda není. Aby se to odráželo, mohl by být přijatý argument typu <xref:System.ReadOnlyMemory%601>. Další informace o <xref:System.ReadOnlyMemory%601>naleznete v tématu [Rule #2: použijte ReadOnlySpan\<t> nebo ReadOnlyMemory\<t>, pokud by měla být vyrovnávací paměť jen pro čtení](#rule-2).

### <a name="ownerless-memoryt-instances"></a>Instance> paměti\<pro vlastní přidaný čas

Můžete vytvořit <xref:System.Memory%601> instanci bez použití <xref:System.Buffers.IMemoryOwner%601>. V takovém případě je vlastnictví vyrovnávací paměti implicitní, nikoli explicitní, a podporuje se jenom model s jedním vlastníkem. Můžete to udělat takto:

- Volání jednoho z <xref:System.Memory%601> konstruktorů přímo, předání v `T[]`, jak je uvedeno v následujícím příkladu.

- Voláním metody rozšíření [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) pro vytvoření `ReadOnlyMemory<char>` instance.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metoda, která zpočátku vytvoří <xref:System.Memory%601> instanci, je implicitní vlastník vyrovnávací paměti. Vlastnictví nelze přenést do žádné jiné součásti, protože není k dispozici žádná <xref:System.Buffers.IMemoryOwner%601> instance pro usnadnění přenosu. (Jako alternativu můžete také představovat, že systém uvolňování paměti modulu runtime vlastní vyrovnávací paměť, a všechny metody pouze využívají vyrovnávací paměť.)

## <a name="usage-guidelines"></a>Pokyny k používání

Vzhledem k tomu, že blok paměti je vlastněn, ale má být předán více komponentám, některé z nich mohou fungovat současně na konkrétní blok paměti, je důležité vytvořit pokyny pro použití obou <xref:System.Memory%601> i. <xref:System.Span%601>  Pokyny jsou nezbytné z těchto důvodů:

- Je možné, že komponenta uchovává odkaz na blok paměti poté, co ho jeho vlastník uvolnil.

- Je možné, že komponenta pracuje na vyrovnávací paměti současně s tím, že na ní jiná komponenta pracuje, v procesu poškození dat ve vyrovnávací paměti.

- I když je vyhrazená sada pro <xref:System.Span%601> optimalizaci výkonu a dává <xref:System.Span%601> preferovaný typ pro provoz na bloku paměti, je také předmětům <xref:System.Span%601> některých hlavních omezení. Je důležité znát, kdy použít <xref:System.Span%601> a kdy použít. <xref:System.Memory%601>

Níže jsou naše doporučení pro úspěšné používání <xref:System.Memory%601> a související typy. Doprovodné materiály, které <xref:System.Memory%601> se <xref:System.Span%601> vztahují na a <xref:System.ReadOnlyMemory%601> platí <xref:System.ReadOnlySpan%601> i v případě, že výslovně nebereme jinak.

**#1 pravidla: v případě synchronního rozhraní API použijte\<místo parametru> paměti\<t, pokud je to možné, možnost span t>.**

<xref:System.Span%601>je všestrannější než <xref:System.Memory%601> a může představovat širší škálu souvislých vyrovnávacích pamětí. <xref:System.Span%601>nabízí také lepší výkon než <xref:System.Memory%601>. <xref:System.Memory%601.Span?displayProperty=nameWithType> Nakonec můžete použít vlastnost k převedení <xref:System.Memory%601> instance na a <xref:System.Span%601>, i když převod span\<t>-to-Memory\<> není možné. Takže v případě, že se volající mají <xref:System.Memory%601> instance, budou moci volat metody s <xref:System.Span%601> parametry přesto.

Použití parametru typu <xref:System.Span%601> místo typu <xref:System.Memory%601> také vám pomůže napsat správnou implementaci využívající metodu. Automaticky získáte kontroly za běhu, abyste se ujistili, že se nepokoušíte o přístup k vyrovnávací paměti nad zapůjčením vaší metody (Další informace najdete později).

V některých případech budete muset místo <xref:System.Memory%601> <xref:System.Span%601> parametru použít parametr, a to i v případě, že jste plně synchronně. Možná rozhraní API, které zabíráte <xref:System.Memory%601> , přijímá jenom argumenty. Je to v pořádku, ale mějte na paměti, že při použití <xref:System.Memory%601> synchronně dochází k kompromisům.

<a name="rule-2" />

**#2 pravidla: použijte ReadOnlySpan\<t> nebo ReadOnlyMemory\<t>, pokud by měla být vyrovnávací paměť jen pro čtení.**

V předchozích příkladech `DisplayBufferToConsole` metoda čte pouze z vyrovnávací paměti; neupravuje obsah vyrovnávací paměti. Signatura metody by se měla změnit na následující.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

V případě, že toto pravidlo a pravidlo kombinujeme #1, můžeme ještě lepší a přepsat signaturu metody následujícím způsobem:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

Metoda `DisplayBufferToConsole` teď funguje s prakticky všemi typy vyrovnávací paměti, které lze `T[]`předcházet:, úložiště přidělené [stackalloc](../../csharp/language-reference/operators/stackalloc.md)a tak dále. Můžete dokonce předat <xref:System.String> přímo na!

**#3 pravidla: Pokud vaše metoda přijímá paměť\<t> a vrátí `void`, nemusíte po návratu metody\<použít instanci> paměti t.**

To se týká konceptu zapůjčení uvedeného výše. Zapůjčení metody vracející anulování <xref:System.Memory%601> instance začíná při zadání metody a končí při ukončení metody. Vezměte v úvahu následující příklad, který `Log` volá smyčku na základě vstupu z konzoly.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Pokud `Log` je plně synchronní metodou, bude tento kód fungovat podle očekávání, protože v daném okamžiku existuje pouze jeden aktivní spotřebitel instance paměti.
Ale představte `Log` si, že tato implementace má tuto implementaci.

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

V této implementaci porušuje své zapůjčení, `Log` protože se stále pokouší použít <xref:System.Memory%601> instanci na pozadí po vrácení původní metody. `Main` Metoda by mohla při `Log` pokusech o čtení z ní načítat vyrovnávací paměť, což by mohlo vést k poškození dat.

Tuto chybu lze vyřešit několika způsoby:

- `Log` Metoda může vracet <xref:System.Threading.Tasks.Task> namísto `void`, jako následující implementace `Log` metody.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log`místo toho je možné implementovat následujícím způsobem:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**#4 pravidla: Pokud vaše metoda přijímá> paměti\<t a vrátí úlohu, nemusíte po přechodu úlohy do stavu\<terminálu používat instanci t> paměti.**

Toto je pouze asynchronní varianta pravidla #3. `Log` Metodu z předchozího příkladu můžete zapsat takto, aby splňovala toto pravidlo:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

V tomto případě "stav terminálu" znamená, že se úloha přechází do stavu dokončeno, chyba nebo zrušeno. Jinými slovy "Terminal State" znamená "cokoli, co by způsobilo, že se očekává, že se má vyvolávat nebo pokračovat v provádění."

Tento návod se vztahuje na metody, <xref:System.Threading.Tasks.Task>které <xref:System.Threading.Tasks.Task%601>vracejí <xref:System.Threading.Tasks.ValueTask%601>,, nebo podobného typu.

**#5 pravidla: Pokud váš konstruktor přijímá paměť\<T,> jako parametr, předpokládá se, že metody instance na vytvořeném objektu budou spotřebiteli instance\<> paměti t.**

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

V `OddValueExtractor` tomto případě konstruktor přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže samotný konstruktor je příjemcem `ReadOnlyMemory<int>` instance a všechny metody instance vrácené hodnoty jsou také příjemci původní `ReadOnlyMemory<int>` instance. To znamená, `TryReadNextOddValue` že `ReadOnlyMemory<int>` instance spotřebovává, i když instance není předána přímo `TryReadNextOddValue` metodě.

**#6 pravidla: Pokud máte ve svém typu nastavitelnou vlastnost typu paměť\<t> (nebo ekvivalentní metodu instance), předpokládá se, že metody instance tohoto objektu budou spotřebiteli instance> paměti\<t.**

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

**#7 pravidla: Pokud máte odkaz na>\<IMemoryOwner T, je potřeba, abyste ho odstranili nebo přenesli jeho vlastnictví (ale ne obojí).**

Vzhledem k <xref:System.Memory%601> tomu, že instance může být zajištěna buď spravovanou, nebo nespravovanou pamětí <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> , musí vlastník zavolat, <xref:System.Memory%601> až bude dokončena práce na instanci. Alternativně může vlastník přenést vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou komponentu. v takovém případě se součást získání bude zodpovědná za volání <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> v příslušné době (Další informace najdete později).

Nepodaří-li <xref:System.Buffers.MemoryPool%601.Dispose%2A> se zavolat metodu, může dojít k nevrácení nespravované paměti nebo jinému snížení výkonu.

Toto pravidlo platí také pro kód, který volá metody objektu <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>pro vytváření, jako je. Volající se stane vlastníkem vráceného <xref:System.Buffers.IMemoryOwner%601> a zodpovídá za odstranění instance po dokončení.

**#8 pravidla: Pokud máte na ploše rozhraní\<API parametr> IMemoryOwner T, přijímáte vlastnictví této instance.**

Přijetí instance tohoto typu signalizuje, že vaše komponenta zamýšlí převzít vlastnictví této instance. Vaše komponenta se bude zodpovědná za řádné vyřazení podle pravidla #7.

Jakákoli komponenta, která přenáší vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance do jiné komponenty, by již neměla používat tuto instanci po dokončení volání metody.

> [!IMPORTANT]
> Pokud váš konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho typ by měl implementovat <xref:System.IDisposable>a vaše <xref:System.IDisposable.Dispose%2A> metoda by měla volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.

**#9 pravidla: Pokud zabalíte synchronní metodu volání nespravovaného volání, rozhraní API by mělo\<jako parametr přijmout> s rozsahem T.**

V souladu s pravidly #1 <xref:System.Span%601> je všeobecně správný typ, který se má použít pro synchronní rozhraní API. Instance můžete připnout <xref:System.Span%601> prostřednictvím [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) klíčového slova, jak je uvedeno v následujícím příkladu.

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

V předchozím příkladu `pbData` může mít hodnotu null, pokud je například vstupní rozpětí prázdné. Pokud exportovaná metoda naprosto vyžaduje, `pbData` aby byla nenulová, i když `cbData` je hodnota 0, metoda může být implementována takto:

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

**#10 pravidla: Pokud zabalíte asynchronní metodu volání nespravovaného volání, rozhraní API by mělo\<jako parametr přijmout> paměti T.**

Vzhledem k tomu, že [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) nelze použít klíčové slovo v rámci asynchronních <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> operací, použijte <xref:System.Memory%601> metodu pro připnutí instancí bez ohledu na druh souvislé paměti, kterou instance představuje. Následující příklad ukazuje, jak použít toto rozhraní API k provedení asynchronního volání volání nespravovaného volání.

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
    var actualState = (MyCompletedCallbackState)(handle.Target);
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
