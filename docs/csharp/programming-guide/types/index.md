---
title: 'Typy – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - 'value types [C#]'
  - 'reference types [C#]'
  - 'types [C#]'
  - 'C# language, data types'
  - 'common type system [C#]'
  - 'data types [C#]'
  - 'C# language, types'
  - 'strong typing [C#]'
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
---
# <a name="types-c-programming-guide"></a>Typy (Průvodce programováním v C#)
## <a name="types-variables-and-values"></a>Typy, proměnných a hodnot  
 C# je silně typovaný jazyk. Všechny proměnné a konstanty mají typ, stejně jako každý výraz, který se vyhodnotí na hodnotu. Každý podpis metody Určuje typ každého vstupního parametru a vracené hodnoty. Knihovny tříd .NET definuje sadu předdefinovaných číselných typů, jakož i složitější typy, které představují širokou škálu logických konstrukcí, jako je například systém souborů, připojení k síti, kolekce a pole objektů a data. Typické programu v C# používá typy z knihovny tříd i uživatelské typy, které modelují koncepty, které jsou specifické pro problematiku programu.  
  
 Informace uložené v typu může patřit také následující:  
  
-   Prostor úložiště, který vyžaduje proměnnou typu.  
  
-   Maximální a minimální hodnoty, které mohou představovat.  
  
-   Členy (metody, pole, události atd.), které obsahuje.  
  
-   Základní typ, který dědí z.  
  
-   Umístění, kde bude přidělena paměť pro proměnné v době běhu.  
  
-   Typy operací, které jsou povoleny.  
  
 Kompilátor používá informace o typu, abyste měli jistotu, že jsou všechny operace, které jsou prováděny ve vašem kódu *bezpečnost typů*. Například, pokud deklarujete proměnnou typu [int](../../../csharp/language-reference/keywords/int.md), kompilátor umožňuje také použít proměnné a operace odčítání. Pokud se pokusíte provést tyto stejné operace na proměnnou typu [bool](../../../csharp/language-reference/keywords/bool.md), kompilátor vygeneruje chybu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]  
  
> [!NOTE]
>  Vývojáře v C a C++, Všimněte si, že v jazyce C#, [bool](../../../csharp/language-reference/keywords/bool.md) není převoditelná na [int](../../../csharp/language-reference/keywords/int.md).  
  
 Kompilátor vloží informace o typu do spustitelného souboru jako metadata. Common language runtime (CLR) používá tato metadata za běhu, aby byla dále podpořena bezpečnost typů, při přidělování a uvolňování paměti.  
  
### <a name="specifying-types-in-variable-declarations"></a>Určení typů v deklaracích proměnných  
 Pokud deklarujete proměnnou nebo konstantní v programu, musíte buď určit její typ nebo použít [var](../../../csharp/language-reference/keywords/var.md) – klíčové slovo, abyste umožnili kompilátoru odvodit typ. Následující příklad ukazuje některé deklarace proměnných, které používají předdefinované číselné typy a komplexní typy definované uživatelem:  
  
 [!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]  
  
 Typy parametrů metod a vrácené hodnoty jsou uvedeny v podpisu metody. Následující podpis představuje metodu, která vyžaduje [int](../../../csharp/language-reference/keywords/int.md) jako vstupní argument a vrátí řetězec:  
  
 [!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]  
  
 Jakmile je proměnná deklarována, nemůže být znovu deklarována s novým typem a nelze jí přiřadit hodnotu, která není kompatibilní s příslušným deklarovaným typem. Například nelze deklarovat [int](../../../csharp/language-reference/keywords/int.md) a přiřadit mu hodnotu typu Boolean [true](../../../csharp/language-reference/keywords/true-literal.md). Hodnoty však lze převést na jiné typy, například když jsou přiřazeny nové proměnné nebo předány jako argumenty metody. A *převod typu* fakturuje se u tohoto nezpůsobí ztrátu dat probíhá automaticky kompilátorem. Vyžaduje převod, který může způsobit ztrátu dat *přetypování* ve zdrojovém kódu.  
  
 Další informace najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="built-in-types"></a>Vestavěné typy  
 Jazyk C# poskytuje standardní sadu předdefinovaných číselných typů k vyjádření celočíselných hodnot, s plovoucí desetinnou čárkou hodnoty bodů, logických výrazů, znaků textu, desetinných míst a dalších typů dat. Existují také vestavěné `string` a `object` typy. Toto jsou k dispozici pro použití v libovolném programu C#. Další informace o předdefinovaných typech naleznete v tématu [referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Vlastní typy  
 Můžete použít [struktura](../../../csharp/language-reference/keywords/struct.md), [třídy](../../../csharp/language-reference/keywords/class.md), [rozhraní](../../../csharp/language-reference/keywords/interface.md), a [výčtu](../../../csharp/language-reference/keywords/enum.md) konstrukce k tvorbě vlastních typů. Samotné knihovny tříd .NET je kolekce vlastních typů společnosti Microsoft, můžete použít ve svých vlastních aplikacích. Nejčastěji používané typy v knihovně tříd jsou standardně k dispozici v libovolném programu C#. Ostatní jsou k dispozici pouze v případě, že explicitně přidáte odkaz na sestavení, ve kterém jsou definovány. Poté, co kompilátor získá odkaz na sestavení, můžete deklarovat proměnné (a konstanty) typů deklarovaných v daném sestavení ve zdrojovém kódu. Další informace najdete v tématu [knihovny tříd .NET](../../../standard/class-library-overview.md).  
  
## <a name="the-common-type-system"></a>Obecný systém typů  
 Je důležité porozumět dvěma základním principům systému typu v rozhraní .NET:  
  
-   Podporuje princip dědičnosti. Typy lze odvodit z jiných typů nazývaných *základní typy*. Odvozený typ zdědí (s určitými omezeními) metody, vlastnosti a ostatní členy základního typu. Základní typ lze odvozovat z některých jiných typů, ve kterém případě odvozený typ dědí členy obou základních typů v hierarchii dědičnosti. Všechny typy včetně předdefinovaných číselných typů, jako například <xref:System.Int32?displayProperty=nameWithType> (C# – klíčové slovo: [int](../../../csharp/language-reference/keywords/int.md)), jsou odvozeny výsledku z jednoho základního typu, které jsou <xref:System.Object?displayProperty=nameWithType> (C# – klíčové slovo: [objekt](../../../csharp/language-reference/keywords/object.md)). Tato hierarchie jednotného typu se nazývá [obecný systém typů](../../../standard/base-types/common-type-system.md) (CTS). Další informace o dědičnosti v C# najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
-   Každý typ v CTS je definována buď jako *typ hodnoty* nebo *odkazovat na typ*. To zahrnuje všechny vlastní typy v knihovně tříd rozhraní .NET a také vlastní uživatelem definované typy. Typy, které definujete pomocí [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo jsou typy hodnot; předdefinované číselné typy jsou `structs`. Typy, které definujete pomocí [třídy](../../../csharp/language-reference/keywords/class.md) – klíčové slovo jsou referenční typy. Typy odkazů a typy hodnot mají jiná pravidla pro kompilaci a jiné chování za běhu.  
  
 Následující ilustrace znázorňuje vztah mezi typy hodnot a odkazové typy v CTS.

 Následující obrázek ukazuje typy hodnot a odkazové typy v CTS: 
  
  
 ![Snímek obrazovky, že ukazuje CTS typy hodnot a typy odkazů.](./media/index/value-reference-types-common-type-system.png)  
  
> [!NOTE]
>  Uvidíte, že nejčastěji používané typy jsou všechny uspořádány v <xref:System> oboru názvů. Obor názvů, ve kterém je obsažen typ, nemá však žádný vztah k tom, zda je hodnota typu nebo typu odkazu.  
  
### <a name="value-types"></a>Typy hodnot  
 Typy hodnot jsou odvozeny z <xref:System.ValueType?displayProperty=nameWithType>, která je odvozena z <xref:System.Object?displayProperty=nameWithType>. Typy, které jsou odvozeny z <xref:System.ValueType?displayProperty=nameWithType> mají zvláštní chování v modulu CLR. Hodnoty typových proměnných přímo obsahují své hodnoty, což znamená, že paměť je přidělena vnitřně v jakémkoli kontextu je proměnná deklarována. Neexistuje samostatné přidělení haldy nebo zařazení kolekce paměti pro proměnné typu hodnoty.  
  
 Existují dvě kategorie typů hodnot: [struktura](../../../csharp/language-reference/keywords/struct.md) a [výčtu](../../../csharp/language-reference/keywords/enum.md).  
  
 Předdefinované číselné typy jsou struktury a mají vlastnosti a metody, které dostanete:  
  
```csharp  
// Static method on type byte.  
byte b = byte.MaxValue;
```  
  
 Ale deklarujete je a přiřadit jim hodnoty tak jako by byly jednoduché neagregované typy:  
  
```csharp  
byte num = 0xA;  
int i = 5;  
char c = 'Z';  
```  
  
 Typy hodnot jsou *zapečetěné*, což znamená, že, například, že nemůžete odvodit typ z <xref:System.Int32?displayProperty=nameWithType>, a nemůžete definovat strukturu pro dědění z jakéhokoli uživatelsky definované třídy nebo struktury, protože struktura může dědit jedině z <xref:System.ValueType?displayProperty=nameWithType> . Strukturu však můžete implementovat jednu nebo více rozhraní. Můžete obsadit typ struktury na libovolný typ rozhraní, který implementuje; To způsobí, že *zabalení* operace zalomí strukturu uvnitř odkazu typu objektu na spravované haldě. K operaci zabalení dochází při předání typu hodnoty metodě, která přijímá <xref:System.Object?displayProperty=nameWithType> nebo některý typ jako vstupní parametr rozhraní. Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
 Můžete použít [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo k tvorbě vlastních typů vlastní hodnotu. Obvykle struktura slouží jako kontejner pro malou skupinu příbuzných proměnných, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Další informace o strukturách naleznete v tématu [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md). Další informace o typech hodnot v rozhraní .NET najdete v tématu [hodnotách](../../../csharp/language-reference/keywords/value-types.md).  
  
 Další kategorie typů hodnot je [výčtu](../../../csharp/language-reference/keywords/enum.md). Výčet definuje sadu pojmenovaných integrálních konstant. Například <xref:System.IO.FileMode?displayProperty=nameWithType> výčtu v knihovně tříd rozhraní .NET obsahuje sadu s názvem konstantní celá čísla, které určují, jak by měl být soubor otevřen. Jak je znázorněno v následujícím příkladu je definována:  
 
 [!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]  
  
 `System.IO.FileMode.Create` – Konstanta má hodnotu 2. Název však má mnohem větší smysl pro člověka při čtení zdrojového kódu a z toho důvodu je lepší používat místo čísel konstantní literální čísla. Další informace naleznete v tématu <xref:System.IO.FileMode?displayProperty=nameWithType>.  
  
 Všechny výčty dědí z <xref:System.Enum?displayProperty=nameWithType>, který dědí z <xref:System.ValueType?displayProperty=nameWithType>. Všechna pravidla, které se vztahují na struktury se vztahují také na výčty. Další informace o výčtech naleznete v tématu [výčtové typy](../../../csharp/programming-guide/enumeration-types.md).  
  
### <a name="reference-types"></a>Typy odkazů  
 Typ, který je definován jako [třídy](../../../csharp/language-reference/keywords/class.md), [delegovat](../../../csharp/language-reference/keywords/delegate.md), pole, nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md) je *odkazovat na typ*. V době běhu při deklarování proměnné typu odkazu proměnná obsahuje hodnotu [null](../../../csharp/language-reference/keywords/null.md) dokud explicitně nevytvoříte objekt s použitím [nové](../../../csharp/language-reference/keywords/new.md) operátor nebo jí nepřiřadíte objekt, který je vytvořen jinde pomocí `new`, jak je znázorněno v následujícím příkladu:
  
```csharp  
MyClass mc = new MyClass();  
MyClass mc2 = mc;  
```  
   Rozhraní musí být inicializováno spolu s objektem třídy, který jej implementuje. Pokud `MyClass` implementuje `IMyInterface`, můžete vytvořit instanci `IMyInterface` jak je znázorněno v následujícím příkladu:  
  
```csharp  
IMyInterface iface = new MyClass();  
```  
  
 Při vytvoření objektu je paměť přidělena na spravované haldě a proměnná obsahuje pouze odkaz na umístění objektu. Typy na spravované haldě zdržovat při přidělování i při jejich převzetí pomocí funkce správy automatické paměti modulu CLR, která se nazývá *uvolňování*. Nicméně uvolňování paměti je také vysoce optimalizováno a ve většině případů nedojde k vytvoření problému s výkonem. Další informace o uvolňování paměti naleznete v tématu [Automatická správa paměti](../../../standard/automatic-memory-management.md).  
  
 Všechna pole jsou typy odkazů, i když jsou jejich prvky typy hodnot. Pole implicitně odvozují ze <xref:System.Array?displayProperty=nameWithType> třídy, ale deklarujete a používáte je se zjednodušenou syntaxí, která je k dispozici v jazyce C#, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]  
  
 Typy odkazu plně podporují dědičnost. Při vytváření třídy můžete dědit ze kteréhokoli rozhraní nebo třídu, která není definován jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), a jiné třídy mohou dědit z vaší třídy a přepsat vaše virtuální metody. Další informace o tom, jak vytvořit vlastní třídy naleznete v tématu [třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md). Další informace o dědičnosti a virtuálních metodách, naleznete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="types-of-literal-values"></a>Typů hodnot literálů  
 V jazyce C# hodnoty literálu získávají typ z kompilátoru. Můžete určit, jak by měly být typu číselný literál přidáním písmene na konci čísla. Například chcete-li určit, že by měl hodnotou 4,56 zacházet jako s float, přidejte k "f" nebo "F" za číslo: `4.56f`. Pokud není připojeno žádné písmeno, kompilátor odvodí typ literál. Další informace o tom, které mohou být typy specifikovat písmennými příponami, najdete v referenčních stránkách pro jednotlivé typy v [hodnotách](../../../csharp/language-reference/keywords/value-types.md).  
  
 Vzhledem k tomu, že jsou literály typovány a všechny typy jsou nakonec odvozeny z <xref:System.Object?displayProperty=nameWithType>, můžete psát a kompilovat kód následujícím:  
  
 [!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]  
  
## <a name="generic-types"></a>Obecné typy  
 Typ lze deklarovat s jedním nebo více *parametry typu* , které slouží jako zástupný symbol pro skutečný typ ( *konkrétní typ*), že kód klienta poskytne při vytváření instance daného typu. Tyto typy jsou označovány jako *obecných typů*. Například typ formátu .NET <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> má jeden parametr typu, které podle konvence je označen názvem *T*. Při vytváření instance typu, je třeba zadat typ objektů, které budou obsahovat seznam, například řetězec:  
 
```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```
 Použití parametru typu umožňuje znovu použít stejné třídy pro uložení libovolného typu prvku, aniž by bylo nutné převést každý prvek na [objekt](../../../csharp/language-reference/keywords/object.md). Obecné třídy kolekcí se nazývají *silně typované kolekce* protože kompilátor zná konkrétní typ prvků kolekci a může vyvolat chyby při kompilaci, pokud, například pokusu o přidání celého čísla `stringList` objekt v předchozím příkladu. Další informace najdete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).  
  
## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Implicitní typy, anonymní typy a typy s možnou hodnotou Null  
 Jak bylo uvedeno dříve, můžete implicitně zadat místní proměnnou (ale ne členy třídy) pomocí [var](../../../csharp/language-reference/keywords/var.md) – klíčové slovo. Proměnná stále přijímá typ v době kompilace, ale typ je poskytován kompilátorem. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 V některých případech je nevhodné vytvářet pojmenované typy pro jednoduché sady souvisejících hodnot, které nezamýšlíte ukládat ani přenášet mimo hranice metody. Můžete vytvořit *anonymní typy* pro tento účel. Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Typy běžných hodnot nemohou mít hodnotu [null](../../../csharp/language-reference/keywords/null.md). Můžete však vytvořit typy s možnou hodnotou Null přidáním `?` po typu. Například `int?` je `int` typ, který může mít také hodnotu [null](../../../csharp/language-reference/keywords/null.md). V CTS jsou typy připouštějící hodnotu Null instancemi obecného typu struktury <xref:System.Nullable%601?displayProperty=nameWithType>. Typy s možnou hodnotou Null jsou zvláště užitečné při předávání dat do a z databáze, ve kterých mohou být číselné hodnoty null. Další informace najdete v tématu [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v následujících tématech:  
  
-   [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
  
-   [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
  
-   [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
  
-   [Obecné typy](../../../csharp/programming-guide/generics/index.md)  

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Převod datových typů XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)
