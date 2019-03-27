---
title: Paměť<T> a rozpětí<T> pokyny k používání
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e942b3f6f6572c05d42a0267f98e6c876a113616
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504337"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Paměť\<T > a rozpětí\<T > Pokyny k používání

.NET core obsahuje několik typů, které představují libovolné souvislých oblasti paměti. .NET core 2.0 zavedené <xref:System.Span%601> a <xref:System.ReadOnlySpan%601>, které jsou zjednodušené paměti vyrovnávacích pamětí, které mohou být se opírá o spravované nebo nespravované paměti. Protože tyto typy mohou být uloženy do zásobníku, jsou vhodná pro řadu scénářů, včetně volání asynchronní metody. .NET core 2.1 přidává několik dalších typů, včetně <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, a <xref:System.Buffers.MemoryPool%601>. Stejně jako <xref:System.Span%601>, <xref:System.Memory%601> a jeho souvisejících typů může být zálohovaný pamětí spravovaných i nespravovaných. Na rozdíl od <xref:System.Span%601>, <xref:System.Memory%601> se dají ukládat jenom na spravované haldě.

Obě <xref:System.Span%601> a <xref:System.Memory%601> vyrovnávací paměti strukturovaných dat, který lze použít v kanálech. To znamená, že jsou navržené tak, že některá nebo všechna data lze efektivněji předat komponenty v kanálu, které mohl zpracovat a volitelně změňte vyrovnávací paměti. Protože <xref:System.Memory%601> a jeho souvisejících typů je přístupný podle více komponent nebo ve víc vláknech je důležité, že vývojáři postupovali podle některé standardní použití pokyny pro vytvoření robustního kódu.

## <a name="owners-consumers-and-lifetime-management"></a>Vlastníci, uživatele a správa životního cyklu

Protože vyrovnávací paměti mohou být předány kolem mezi rozhraním API, a protože vyrovnávací paměti v některých případech je přístupný z více vláken, je důležité vzít v úvahu Správa životního cyklu. Existují tři základní koncepty:

- **Vlastnictví**. Vlastník instance vyrovnávací paměti je zodpovědný za správu životního cyklu, včetně zničení vyrovnávací paměti, když se už používá. Všechny vyrovnávací paměti mají jednoho vlastníka. Obecně vlastníka je komponenta, která vytvoří vyrovnávací paměti nebo vyrovnávací paměti, který přijal od objektu factory. Lze také převést vlastnictví; **Komponenty A** můžete opustit ovládacího prvku vyrovnávací paměti pro **součást B**, v tomto okamžiku **komponenty A** může již nebudete používat vyrovnávací paměť, a **součást B**  zodpovědná za zničení vyrovnávací paměti, když se už používá.

- **Spotřeba**. Příjemce instanci vyrovnávací paměti může používat instanci vyrovnávací paměti čtení z něj a může být zápis do něj. Vyrovnávací paměti může mít jednoho příjemce současně, pokud je k dispozici některé externí synchronizační mechanismus. Upozorňujeme, že aktivní příjemce vyrovnávací paměť není nutně vlastníka přípravné vyrovnávací paměti.

- **Zapůjčení**. Zapůjčení je doba, kterou může být příjemce vyrovnávací paměti jednotlivých součástí.

Následující příklad kódu pseudo znázorňuje tyto tři pojmy. Zahrnuje `Main` metodu, která vytvoří instanci <xref:System.Memory%601> vyrovnávací paměti typu <xref:System.Char>, volání `WriteInt32ToBuffer` metody zapsat do vyrovnávací paměti a pak volá řetězcové vyjádření celého čísla `DisplayBufferToConsole` metodu pro zobrazení hodnoty vyrovnávací paměť.

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

`Main` Metoda vytvoří vyrovnávací paměti (v tomto případě <xref:System.Span%601> instance) a proto je jeho vlastníkem. Proto `Main` zodpovídá za zničení vyrovnávací paměti, když se už používá. Dělá to pomocí volání do vyrovnávací paměti <xref:System.Span%601.Clear?displayProperty=nameWithType> metody. ( <xref:System.Span%601.Clear> Metoda tady ve skutečnosti Vymaže vyrovnávací paměti; <xref:System.Span%601> struktury ve skutečnosti nemá metodu, která odstraní vyrovnávací paměti.)

Vyrovnávací paměť obsahuje dva zákazníky `WriteInt32ToBuffer` a `DisplayBufferToConsole`. Existuje pouze jeden příjemce najednou (první `WriteInt32ToBuffer`, pak `DisplayBufferToConsole`), a ani spotřebitelů vlastní vyrovnávací paměti. Všimněte si také, zda "příjemce" v tomto kontextu není implikují zobrazení jen pro čtení vyrovnávací paměti; příjemci přípravné vyrovnávací paměti obsah, upravit jako `WriteInt32ToBuffer` nedojde, pokud tento parametr zadaný zobrazení pro čtení a zápis vyrovnávací paměti.

`WriteInt32ToBuffer` Metoda má zapůjčený (může spotřebovat) vyrovnávací paměť mezi začátkem volání metody a čas, metoda vrátí. Obdobně `DisplayBufferToConsole` má zapůjčený vyrovnávací paměti, zatímco je prováděna a zapůjčení se uvolní, když metoda unwinds. (Neexistuje žádné rozhraní API pro správu zapůjčení; "pronájmu" což je koncepční.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Paměť\<T > a model vlastníka/konzumenta najdete

Jako [vlastníky, uživatele a správa životního cyklu](#owners-consumers-and-lifetime-management) část poznámky, vyrovnávací paměti má vždy vlastníka. .NET core podporuje dva modely vlastnictví:

- Model, který podporuje jeden vlastnictví. Vyrovnávací paměť nemá jednoho vlastníka pro celou dobu života.

- Model, který podporuje převod vlastnictví. Vlastnictví vyrovnávací paměti lze přenést z jeho původní vlastníkovi (autorovi) do jiné součásti, která se pak stane zodpovědný za správu životního cyklu přípravné vyrovnávací paměti. Tento vlastník zase můžete převést vlastnictví na jiné součásti a tak dále.

Můžete použít <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> rozhraní explicitně spravovat vlastnictví vyrovnávací paměti. <xref:System.Buffers.IMemoryOwner%601> podporuje oba modely vlastnictví. Komponenta, která má <xref:System.Buffers.IMemoryOwner%601> odkaz na vlastní vyrovnávací paměti. Následující příklad používá <xref:System.Buffers.IMemoryOwner%601?> instance tak, aby odrážely vlastnictví <xref:System.Memory%601> vyrovnávací paměti.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Můžeme také napsat v tomto příkladu se [ `using` ](~/docs/csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

V tomto kódu:

- `Main` Metoda obsahuje odkaz na <xref:System.Buffers.IMemoryOwner%601> instance, takže `Main` metoda je vlastníkem vyrovnávací paměti.

- `WriteInt32ToBuffer` a `DisplayBufferToConsole` metody přijímají xref:System.Memory%601 > jako veřejné rozhraní API. Proto jsou příjemci vyrovnávací paměti. A jsou pouze použít jeden po druhém.

I když `WriteInt32ToBuffer` metoda se má zapsat hodnotu do vyrovnávací paměti, `DisplayBufferToConsole` není metoda. Tyto změny projeví na ho může přijali argument typu <xref:System.ReadOnlyMemory%601>. Další informace o <xref:System.ReadOnlyMemory%601>, naleznete v tématu [pravidlo č. 2: Použít ReadOnlySpan\<T > nebo ReadOnlyMemory\<T > Pokud vyrovnávací paměť by měl být jen pro čtení](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"Ownerless" paměti\<T > instancí

Můžete vytvořit <xref:System.Memory%601> instance bez použití <xref:System.Buffers.IMemoryOwner%601>. V takovém případě vlastnictví vyrovnávací paměti je implicitní namísto explicitního a pouze jednoho vlastníka model se nepodporuje. Uděláte to tak:

- Volání jedné z <xref:System.Memory%601> konstruktory přímo, předejte `T[]`, stejně jako v následujícím příkladu.

- Volání [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metodu rozšíření k vytvoření `ReadOnlyMemory<char>` instance.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metoda, která původně vytvoří <xref:System.Memory%601> instance je vlastníkem implicitní vyrovnávací paměti. Vlastnictví nelze přenést na jakoukoli jinou součástí, protože neexistuje žádný <xref:System.Buffers.IMemoryOwner%601> instance pro usnadnění převodu. (Alternativně si můžete také představit, že modul runtime systému uvolňování paměti vlastní vyrovnávací paměti a všechny metody právě využití vyrovnávací paměti.)

## <a name="usage-guidelines"></a>Pokyny k používání

Protože bloku paměti vlastní, ale má být předán více komponent, některé z nich může pracovat současně na blok paměti konkrétní, je důležité stanovit pokyny k používání obou <xref:System.Memory%601> a <xref:System.Span%601>.  Pokyny jsou nezbytné protože:

- Je možné pro součást zachovat odkaz na blok paměti po její vlastník vydala.

- Je možné pro součást ovládajících vyrovnávací paměti ve stejnou dobu, která funguje jiné součásti, v procesu došlo k poškození dat ve vyrovnávací paměti.

- Zatímco povahy přidělený na zásobník <xref:System.Span%601> optimalizuje výkon a zpřístupňuje <xref:System.Span%601> upřednostňovaný typ pro provozování na blok paměti je také Predmety <xref:System.Span%601> na určitá omezení hlavní omezení. Je důležité vědět, kdy se má použít <xref:System.Span%601> a kdy použít <xref:System.Memory%601>.

Toto jsou naše doporučení pro používání úspěšně <xref:System.Memory%601> a jeho souvisejících typů. Mějte na paměti tyto pokyny, které platí pro <xref:System.Memory%601> a <xref:System.Span%601> platí také pro <xref:System.ReadOnlyMemory%601> a <xref:System.ReadOnlySpan%601> Pokud jsme explicitně mějte na paměti jinak.

**Pravidlo #1: Synchronní rozhraní API, použijte Span\<T > místo v paměti\<T > jako parametr, pokud je to možné.**

<xref:System.Span%601> nabízí větší variabilitu než <xref:System.Memory%601> a může představovat širší vyrovnávacích pamětí souvislé paměti. <xref:System.Span%601> také nabízí vyšší výkon než <xref:System.Memory%601>>. Nakonec můžete použít <xref:System.Memory%601.Span?displayProperty=nameWithType> vlastnost převést <xref:System.Memory%601> instance na <xref:System.Span%601>, i když Span\<T > - na - paměti\<T > Převod není možný. Pokud vaše volající náhodou <xref:System.Memory%601> instance, budou moct volat vaše metody s atributem <xref:System.Span%601> parametry přesto.

Pomocí parametru typu <xref:System.Span%601> místo typu <xref:System.Memory%601> také umožňuje zapisovat správná implementace metody náročné. Získáte automaticky kontroluje za kompilace, ujistěte se, že se o přístup k vyrovnávací paměti nad rámec vaše metoda zapůjčení, (více dále).

V některých případech budete muset použít <xref:System.Memory%601> parametr namísto <xref:System.Span%601> parametr, i když jste plně synchronní. Například rozhraní API, které nejvíc potřebujete přijímá pouze <xref:System.Memory%601> argumenty. To je v pořádku, ale mějte na paměti o kompromisech při použití <xref:System.Memory%601> synchronně.

<a name="rule-2" />

**Pravidlo #2: Použít ReadOnlySpan\<T > nebo ReadOnlyMemory\<T > Pokud vyrovnávací paměť by měl být jen pro čtení.**

V předchozích příkladech `DisplayBufferToConsole` metoda četl pouze z vyrovnávací paměti; nezmění obsah vyrovnávací paměti. Podpis metody by měl být změněn na následující.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

Ve skutečnosti Pokud spojili jsme toto pravidlo a pravidlo č. 1, můžeme udělat ještě lépe a přepíše podpis metody následujícím způsobem:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole` Metoda nyní funguje s prakticky všem typ vyrovnávací paměti, který si dokážete představit: `T[]`, přidělit úložiště [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), a tak dále. Dokonce můžete předat <xref:System.String> přímo do ní!

**Pravidlo #3: Pokud vaše metoda přijímá paměti\<T > a vrátí `void`, nesmí používat paměť\<T > po vrácení metodu instance.**

To se týká koncept "pronájmu", již bylo zmíněno dříve. Metody vracející hodnotu void zapůjčení <xref:System.Memory%601> instance začíná, když se zadá metodu a končí při ukončení metodu. Podívejte se na následující příklad volá `Log` ve smyčce založena na vstup z konzoly.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Pokud `Log` je plně synchronní metoda, tento kód se bude chovat podle očekávání, protože existuje pouze jeden příjemce aktivní instance paměti v daném okamžiku.
Ale Představte si, že `Log` má tuto implementaci.

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

V této implementaci `Log` porušuje jeho zapůjčení, protože pořád se pokouší použít <xref:System.Memory%601> instance na pozadí po vrátila původní metodu. `Main` Metoda může mutovat vyrovnávací paměti při `Log` pokouší číst z něj, což by mohlo způsobit poškození dat.

Chcete-li to vyřešit několika způsoby:

- `Log` Metoda může vrátit <xref:System.Threading.Tasks.Task> místo `void`, jako následující provádění `Log` metodu.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log` můžete místo toho implementovat následujícím způsobem:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Pravidlo #4: Pokud vaše metoda přijímá paměťově\<T > a vrátí úlohu, nesmí používat paměť\<T > instance za úkol přejde do konečného stavu.**

Toto je pouze asynchronní variantu pravidlo č. 3. `Log` Metoda z předchozího příkladu je pro dosažení souladu s tímto pravidlem zapisovat následujícím způsobem:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Tady "konečného stavu" znamená, že úkol přejde do dokončeného, došlo k chybě, nebo bylo zrušeno stavu. Jinými slovy znamená, že "konečného stavu" "cokoli, co způsobilo await vyvolat nebo pokračovat v provádění."

Tento návod se vztahuje k metody, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, nebo podobné.

**Pravidlo #5: Pokud váš konstruktor přijímá paměti\<T > jako parametr, metodami instance vytvořený objekt se předpokládá se, že příjemci paměti\<T > instance.**

Vezměte v úvahu v následujícím příkladu:

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

Tady `OddValueExtractor` konstruktor přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže konstruktor samotný je příjemce `ReadOnlyMemory<int>` instance a metodami instance na vrácené hodnoty jsou také příjemci původní `ReadOnlyMemory<int>` instance. To znamená, že `TryReadNextOddValue` využívá `ReadOnlyMemory<int>` instance, i když instance není předána přímo `TryReadNextOddValue` metody.

**Pravidlo #6: Pokud máte nastavitelné paměti\<T >-typovou vlastnost (nebo metodu ekvivalentní instance) na typ, metodami instance tohoto objektu se předpokládá se, že příjemci paměti\<T > instance.**

Toto je pouze typ variant pravidlo č. 5. Toto pravidlo existuje, protože vlastnost setter nebo ekvivalentní metody předpokládá, že jsou pro zaznamenání a uložení jejich vstupech tak metody instance na stejný objekt mohou využívat zaznamenaný stav.

Následující příklad spustí toto pravidlo:

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

**Pravidlo #7: Pokud máte IMemoryOwner\<T > odkaz, je nutné na některé bodu dispose jeho nebo přenos vlastnictví (ale ne obojí).**

Protože <xref:System.Memory%601> instance může být zálohovaný pamětí spravované nebo nespravované, musí volat vlastníka <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> provést, při práci na <xref:System.Memory%601> instance je dokončena. Alternativně může vlastník přenos vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou komponentu, v tomto okamžiku nabývající součást zodpovědná za volání <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> včas (podrobněji dále).

Nepodařilo se zavolat <xref:System.Buffers.MemoryPool%601.Dispose%2A> metoda může vést k nevracení nespravované paměti nebo jiných snížení výkonu.

Toto pravidlo platí také pro kód, který volá metody pro vytváření objektů jako <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>. Volající se stává vlastníkem vráceného <xref:System.Buffers.IMemoryOwner%601> a je zodpovědná za uvolnění instance po dokončení.

**Pravidlo #8: Pokud máte IMemoryOwner\<T > parametr povrchu vaše rozhraní API, abyste přijali vlastnictví této instance.**

Přijímá instanci tohoto typu signalizuje, že vaše komponenta si klade za cíl převzít vlastnictví této instance. Vaše komponenta je zodpovědná za správné odstranění podle pravidlo č. 7.

Jakékoli součásti, která převede vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou komponentu byste již nebudete používat tuto instanci po dokončení volání metody.

> [!IMPORTANT]
> Pokud váš konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho typ by měly implementovat <xref:System.IDisposable>a vaše <xref:System.IDisposable.Dispose%2A> metoda by měla volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.

**Pravidlo #9: Chcete-li obtékání metodu synchronní p/invoke, vaše rozhraní API by měla přijímat rozpětí\<T > jako parametr.**

Podle pravidel č. 1 <xref:System.Span%601> je obecně správný typ má být použit pro synchronní rozhraní API. Můžete připnout <xref:System.Span%601> \<T > přes instance [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) – klíčové slovo, jako v následujícím příkladu.

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

V předchozím příkladu `pbData` může mít hodnotu null, je-li například, vstupní značka je prázdný. Pokud exportované metoda naprosto vyžaduje, aby `pbData` mít hodnotu null, i když `cbData` je 0, metody lze provést následujícím způsobem:

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

**Pravidlo #10: Chcete-li obtékání metody asynchronní p/invoke, vaše rozhraní API by měla přijímat paměti\<T > jako parametr.**

Protože nelze použít [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) – klíčové slovo v asynchronních operací, je použít <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metodu pro Připnutí <xref:System.Memory%601> instancí, bez ohledu na typ, který představuje instanci souvislé paměti. Následující příklad ukazuje, jak pomocí tohoto rozhraní API provádět volání rozhraní asynchronní p/invoke.

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
