---
title: Převod typů v rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- widening conversions
- explicit conversions
- narrowing conversions
- type conversion, about type conversion
- type conversion
- converting types
- narrowing coercion
- Explicit operator
- IConvertible interface
- base types, converting
- op_Implicit method
- widening coercion
- op_Explicit method
- Convert class
- implicit conversions
- Implicit operator
- data types [.NET Framework], converting
ms.assetid: ba36154f-064c-47d3-9f05-72f93a7ca96d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d039e591e1f61a7be18dc224845f82b107d918f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211944"
---
# <a name="type-conversion-in-the-net-framework"></a>Převod typů v rozhraní .NET Framework
<a name="top"></a> Každá hodnota má přidružen typ, který definuje atributy, jako je množství přidělené místo na hodnotě, rozsah možných hodnot, které může mít, a členy, které to umožňují. Mnoho hodnot lze vyjádřit ve formě více než jednoho typu. Například hodnotu 4 lze vyjádřit jako celé číslo nebo jako hodnotu s plovoucí desetinnou čárkou. Převod typu vytvoří hodnotu v novém typu, která je ekvivalentní hodnotě starého typu, ale nutně nezachová identitu (nebo přesnou hodnotu) původního objektu.  
  
 Rozhraní .NET Framework automaticky podporuje následující převody:  
  
-   Převod z odvozené třídy základní třídu. To znamená například, že instance libovolné třídy nebo struktury lze převést na <xref:System.Object> instance.  Tento převod nevyžaduje, aby operátor přetypování či převodu.  
  
-   Převod ze základní třídy zpět na původní odvozené třídy. V jazyce C# vyžaduje tento převod operátor přetypování. V jazyce Visual Basic, vyžaduje `CType` operátor Pokud `Option Strict` zapnutý.  
  
-   Převod z typu, který implementuje rozhraní pro objekt rozhraní, který představuje rozhraní. Tento převod nevyžaduje, aby operátor přetypování či převodu.  
  
-   Převod z rozhraní objektu zpět na původní typ, který implementuje rozhraní.  V jazyce C# vyžaduje tento převod operátor přetypování. V jazyce Visual Basic, vyžaduje `CType` operátor Pokud `Option Strict` zapnutý.  
  
 Kromě těchto automatických převody [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] poskytuje několik funkcí, které podporují převod vlastního typu. Patří mezi ně například:  
  
-   `Implicit` Operátor, který definuje dostupné rozšiřující převody mezi typy. Další informace najdete v tématu [implicitní převod s implicitním operátorem](#implicit_conversion_with_the_implicit_operator) oddílu.  
  
-   `Explicit` Operátor, který definuje dostupné zužující převody mezi typy. Další informace najdete v tématu [explicitní převod s explicitním operátorem](#explicit_conversion_with_the_explicit_operator) oddílu.  
  
-   <xref:System.IConvertible> Rozhraní, které definuje převody na jednotlivé základní datové typy rozhraní .NET Framework. Další informace najdete v tématu [rozhraní IConvertible](#the_iconvertible_interface) oddílu.  
  
-   <xref:System.Convert> Třídu, která poskytuje sadu metod, které implementují <xref:System.IConvertible> rozhraní. Další informace najdete v tématu [Třída Convert](#Convert) oddílu.  
  
-   <xref:System.ComponentModel.TypeConverter> Třídu, která je základní třída, která je možné rozšířit pro podporu převodu určitého typu na jiný typ. Další informace najdete v tématu [Třída TypeConverter](#the_typeconverter_class) oddílu.  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Implicitní převod s implicitním operátorem  
 Rozšiřující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, který má buď více omezený rozsah, nebo více omezený seznam členů než cílový typ. Rozšiřující převody nemohou způsobit ztrátu dat (ačkoliv mohou způsobit ztrátu přesnosti). Vzhledem k tomu, že nemůže dojít ke ztrátě dat, mohou kompilátory zpracovat převod implicitně nebo transparentně, aniž by bylo nutné použít metodu explicitního převodu nebo operátor přetypování.  
  
> [!NOTE]
>  Ačkoli kód, který provede implicitní převod, může volat metodu převodu nebo použít operátor přetypování, není jejich používání vyžadováno kompilátory, které podporují implicitní převody.  
  
 Například <xref:System.Decimal> typů podporuje implicitní převody z <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>, a <xref:System.UInt64> hodnoty. Následující příklad ukazuje některé z těchto implicitních převodů při přiřazování hodnot <xref:System.Decimal> proměnné.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Pokud kompilátor určitého jazyka podporuje vlastní operátory, můžete ve vlastních typech definovat také implicitní převody. Následující příklad uvádí částečnou implementaci datového typu bajty se znaménkem s názvem `ByteWithSign` , který používá reprezentaci znaménkem a řádem. Podporuje implicitní převod <xref:System.Byte> a <xref:System.SByte> hodnoty `ByteWithSign` hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Klientský kód pak může deklarovat `ByteWithSign` proměnnou a přiřaďte ho <xref:System.Byte> a <xref:System.SByte> hodnoty bez provedení jakýchkoli explicitních převodů nebo pomocí jakýchkoli operátorů přetypování, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Zpět na začátek](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Explicitní převod s explicitním operátorem  
 Zužující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, která má buď větší rozsah, nebo větší seznam členů než cílový typ. Vzhledem k tomu, že zužující převod může mít za následek ztrátu dat, kompilátory často vyžadují, aby byl převod vytvořen explicitně prostřednictvím volání metody převodu nebo operátoru přetypování. To znamená, že převod musí být zpracován explicitně v kódu vývojáře.  
  
> [!NOTE]
>  Hlavní účel vyžadujících metodu převodu nebo operátor přetypování pro zužující převody, je informovat vývojáře na možnost ztráty dat nebo <xref:System.OverflowException> tak, že mohou být zpracovány v kódu. Některé kompilátory však mohou tento požadavek zmírnit. Například v aplikaci Visual Basic, pokud `Option Strict` je vypnuto (výchozí nastavení), se pokusí kompilátor jazyka Visual Basic provést zužující převody implicitně.  
  
 Například <xref:System.UInt32>, <xref:System.Int64>, a <xref:System.UInt64> datové typy mají rozsahy, které překročí <xref:System.Int32> datového typu, jak ukazuje následující tabulka.  
  
|Typ|Porovnání s rozsahem Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a <xref:System.Int64.MinValue?displayProperty=nameWithType> je menší než (má větší negativní rozsah než) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Pro zpracování těchto zužujících převodů [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] umožňuje definovat typům `Explicit` operátor. Kompilátory jednotlivých jazyků pak mohou implementovat tento operátor pomocí vlastní syntaxe nebo člen <xref:System.Convert> třída může být volána k provedení převodu. (Další informace o <xref:System.Convert> najdete v tématu [Třída Convert](#Convert) dále v tomto tématu.) Následující příklad ukazuje použití funkcí jazyka ke zpracování explicitního převodu těchto potenciálně mimo rozsah celočíselných hodnot pro <xref:System.Int32> hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Explicitní převody mohou vytvářet různé výsledky v různých jazycích a tyto výsledky se mohou lišit od hodnoty vrácené odpovídající <xref:System.Convert> metody. Například pokud <xref:System.Double> hodnotu 12.63251 je převést na <xref:System.Int32>, jazyka Visual Basic `CInt` metody a rozhraní .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> metoda zaokrouhlí <xref:System.Double> vrátit hodnotu 13, ale jazyka C# `(int)` – operátor ořízne <xref:System.Double> vrátit hodnotu 12. Podobně, C# `(int)` operátor nepodporuje převod logické hodnoty na celé číslo, ale jazyka Visual Basic `CInt` metoda převede hodnotu `true` na hodnotu -1. Na druhé straně <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> metoda převede hodnotu `true` na hodnotu 1.  
  
 Většina kompilátorů umožňuje, aby explicitní převody byly prováděny zkontrolovaným, nebo nezkontrolovaným způsobem. Při provádění kontrolovaného převodu <xref:System.OverflowException> je vyvolána, když hodnota typu pro převod je mimo rozsah cílového typu. Pokud je nezkontrolovaný převod proveden za stejných podmínek, nemusí převod vyvolat výjimku, ale stejné chování bude nedefinováno a může mít za následek nesprávnou hodnotu.  
  
> [!NOTE]
>  V jazyce C#, zkontrolované převody provést pomocí `checked` – klíčové slovo spolu s operátorem přetypování, nebo zadáním `/checked+` – možnost kompilátoru. Naopak nezkontrolované převody lze provést pomocí `unchecked` – klíčové slovo spolu s operátorem přetypování, nebo zadáním `/checked-` – možnost kompilátoru. Ve výchozím nastavení jsou explicitní převody nezkontrolované. V jazyce Visual Basic zkontrolované převody provést zrušením **odebrat kontroly přetečení celých čísel** zaškrtávací políčko v projektu **pokročilé nastavení kompilátoru** dialogové okno, nebo zadáním `/removeintchecks-`– možnost kompilátoru. Naopak nezkontrolované převody lze provést tak, že vyberete **odebrat kontroly přetečení celých čísel** zaškrtávací políčko v projektu **pokročilé nastavení kompilátoru** dialogové okno nebo zadáním `/removeintchecks+`– možnost kompilátoru. Ve výchozím nastavení jsou explicitní převody zkontrolované.  
  
 Následující příklad jazyka C# používá `checked` a `unchecked` klíčových slov pro znázornění rozdílu v chování, pokud je hodnota mimo rozsah <xref:System.Byte> je převedena na <xref:System.Byte>. Zkontrolovaný převod vyvolá výjimku, ale nezkontrolovaný převod přiřadí <xref:System.Byte.MaxValue?displayProperty=nameWithType> k <xref:System.Byte> proměnné.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Pokud konkrétní jazykový kompilátor podporuje vlastní přetížené operátory, můžete ve vlastních typech definovat také explicitní převody. Následující příklad uvádí částečnou implementaci datového typu bajty se znaménkem s názvem `ByteWithSign` , který používá reprezentaci znaménkem a řádem. Podporuje explicitní převod hodnot <xref:System.Int32> a <xref:System.UInt32> hodnoty `ByteWithSign` hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Klientský kód pak může deklarovat `ByteWithSign` proměnnou a přiřaďte ho <xref:System.Int32> a <xref:System.UInt32> hodnoty, pokud přiřazení zahrnují operátor přetypování nebo metodu převodu, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>Rozhraní IConvertible  
 Pro podporu převodu jakéhokoli typu na common language runtime základní typ, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] poskytuje <xref:System.IConvertible> rozhraní. Implementující typ je vyžadován pro následující akce:  
  
-   Metoda, která vrátí <xref:System.TypeCode> implementujícího typu.  
  
-   Metody k převodu implementujícího typu na jednotlivých common language runtime základních typů (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, a tak dále).  
  
-   Zobecněná metoda převodu k převedení instance implementujícího typu na jiný určený typ. Převody, které nejsou podporovány, by měly vyvolat <xref:System.InvalidCastException>.  
  
 Každý common language runtime základního typu (to znamená, <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>, a <xref:System.UInt64>), stejně jako <xref:System.DBNull> a <xref:System.Enum> typy, implementovat <xref:System.IConvertible> rozhraní. Ty jsou však implementace explicitního rozhraní. Metoda převodu lze volat pouze prostřednictvím <xref:System.IConvertible> proměnné rozhraní, jak ukazuje následující příklad. Tento příklad převede <xref:System.Int32> hodnotu na její ekvivalentní <xref:System.Char> hodnotu.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Pokud je požadavek volání metody převodu uplatněn na rozhraní a nikoli na implementující typ, jsou implementace explicitního rozhraní poměrně nákladné. Namísto toho doporučujeme volat odpovídající člen třídy <xref:System.Convert> pro převod mezi common language runtime základních typů. Další informace naleznete v části Další [Třída Convert](#Convert).  
  
> [!NOTE]
>  Kromě <xref:System.IConvertible> rozhraní a <xref:System.Convert> třídy poskytované [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], mohou jednotlivé jazyky převody provádět také poskytnout. Například C# používá operátory přetypování. Jazyk Visual Basic používá funkce převodu implementované kompilátorem, jako `CType`, `CInt`, a `DirectCast`.  
  
 Ve většině případů <xref:System.IConvertible> rozhraní je navržen pro podporu převodu mezi základními typy v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Rozhraní lze však implementovat také pomocí vlastního typu, a podpořit tak převod tohoto typu na vlastní typy. Další informace najdete v části [vlastní převody pomocí metody ChangeType](#ChangeType) dále v tomto tématu.  
  
 [Zpět na začátek](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Třída Convert  
 I když jednotlivých základních typů <xref:System.IConvertible> implementace rozhraní může být volána k provedení převodu typu, volání metod <xref:System.Convert?displayProperty=nameWithType> třídy je doporučené jazykově neutrální způsob, jak převést z jednoho základního typu. Kromě toho <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu lze použít pro převod z vlastního zadaného typu na jiný typ.  
  
### <a name="conversions-between-base-types"></a>Převody mezi základními typy  
 <xref:System.Convert> Třída poskytuje jazykově neutrální způsob převodů mezi základními typy a je k dispozici pro všechny jazyky, které se zaměřují na modul common language runtime. Poskytuje úplnou sadu metod pro rozšiřující i zužující převody a vyvolá výjimku <xref:System.InvalidCastException> pro převody, které nejsou podporovány (například převod hodnoty <xref:System.DateTime> hodnotu na celočíselnou hodnotu). Zužující převody jsou prováděny ve zkontrolovaném kontextu a <xref:System.OverflowException> je vyvolána, pokud převod selže.  
  
> [!IMPORTANT]
>  Vzhledem k tomu, <xref:System.Convert> třída obsahuje metody pro převod do a z jednotlivých základních typů, eliminuje nutnost volání jednotlivých základních typů <xref:System.IConvertible> explicitní implementaci rozhraní.  
  
 Následující příklad ukazuje použití <xref:System.Convert?displayProperty=nameWithType> pro provádění několika rozšiřujících a zužujících převodů mezi základními typy rozhraní .NET Framework.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 V některých případech, zejména při převodu do a z hodnoty s plovoucí desetinnou čárkou, převod může zahrnovat ke ztrátě přesnosti, i když se nevyvolá <xref:System.OverflowException>. Následující příklad znázorňuje tuto ztrátu přesnosti. V prvním případě <xref:System.Decimal> hodnota má nižší přesnost (méně významných číslic) Pokud je převedena na <xref:System.Double>. V druhém případě <xref:System.Double> hodnota je zaokrouhlena ze 42,72 na 43 dokončení převodu.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Pro tabulku se seznamem rozšiřujících i zužujících převodů podporovaných třídou <xref:System.Convert> najdete v tématu [tabulky převodu typů](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>Vlastní převody pomocí metody ChangeType  
 Kromě podpory převodů na jednotlivé základní typy <xref:System.Convert> třídy lze použít pro převod vlastního typu na jeden nebo více předdefinovaných typů. Tento převod se provádí <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metoda, která poté zabalí volání <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> metodu `value` parametr. To znamená, že objekt reprezentovaný rozhraním `value` parametr musí zajišťovat implementaci rozhraní <xref:System.IConvertible> rozhraní.  
  
> [!NOTE]
>  Protože <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> a <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> pomocí metody <xref:System.Type> objekt pro určení cílového typu, ke kterému `value` je převést, můžete používají pro dynamický převod na objekt, jehož typ není znám v době kompilace. Mějte však na paměti, která <xref:System.IConvertible> provádění `value` musí tento převod podporovat.  
  
 Následující příklad znázorňuje možnou implementaci <xref:System.IConvertible> rozhraní, které umožňuje `TemperatureCelsius` má být převeden na objekt `TemperatureFahrenheit` a naopak. Příklad definuje základní třídu, `Temperature`, který implementuje <xref:System.IConvertible> rozhraní a přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> – metoda. Odvozená `TemperatureCelsius` a `TemperatureFahrenheit` třídy každý přepsání `ToType` a `ToString` metody základní třídy.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Následující příklad znázorňuje několik volání těchto <xref:System.IConvertible> implementace převést `TemperatureCelsius` objektů `TemperatureFahrenheit` objekty a naopak.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>Třída TypeConverter  
 Rozhraní .NET Framework umožňuje také definovat konvertor typu pro vlastní typ tím, že rozšíří <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> třídy a přidružením konvertoru typu s daným typem prostřednictvím <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> atribut. Následující tabulka zdůrazňuje rozdíly mezi tímto přístupem a implementací <xref:System.IConvertible> rozhraní pro vlastní typ.  
  
> [!NOTE]
>  Podporu v době návrhu lze pro vlastní typ zajistit pouze tehdy, pokud byl definován konvertor typu.  
  
|Převod pomocí TypeConverter|Převod pomocí IConvertible|  
|------------------------------------|-----------------------------------|  
|Je implementován pro vlastní typ odvozením samostatné třídy z třídy <xref:System.ComponentModel.TypeConverter>. Tato odvozená třída je přidružena s vlastním typem použitím <xref:System.ComponentModel.TypeConverterAttribute> atribut.|Je implementován vlastním typem za účelem převodu. Uživatel typu vyvolá <xref:System.IConvertible> metodu převodu typu.|  
|Lze použít v době návrhu i v době spuštění.|Lze použít pouze v době spuštění.|  
|Používá reflexi; Proto je pomalejší než převod povolený třídou <xref:System.IConvertible>.|Nepoužívá reflexi.|  
|Umožňuje obousměrný převod typu z vlastního typu na jiné datové typy a z jiných datových typů na vlastní typ. Například <xref:System.ComponentModel.TypeConverter> definované pro `MyType` umožňuje převod z `MyType` k <xref:System.String>a z <xref:System.String> k `MyType`.|Umožňuje převod z vlastního typu na jiné datové typy, nikoli však z jiných datových typů na vlastní typ.|  
  
 Další informace o používání převodníků typů pro převod naleznete v tématu <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert?displayProperty=nameWithType>  
- <xref:System.IConvertible>  
- [Tabulky převodu typů](../../../docs/standard/base-types/conversion-tables.md)
