---
title: Převod typů v rozhraní .NET Framework
description: Přečtěte si o převodu typu v .NET, který vytvoří hodnotu v novém typu, který je ekvivalentní hodnotě starého typu, ale nemusí uchovávat identitu originálu.
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
ms.openlocfilehash: 11345081610459dbf053d846aa04369301010732
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769220"
---
# <a name="type-conversion-in-the-net-framework"></a>Převod typů v rozhraní .NET Framework
Každá hodnota má přidružený typ, který definuje atributy, jako je například množství prostoru přiděleného hodnotě, rozsah možných hodnot, které může mít, a členy, které zpřístupňují. Mnoho hodnot lze vyjádřit ve formě více než jednoho typu. Například hodnotu 4 lze vyjádřit jako celé číslo nebo jako hodnotu s plovoucí desetinnou čárkou. Převod typu vytvoří hodnotu v novém typu, která je ekvivalentní hodnotě starého typu, ale nutně nezachová identitu (nebo přesnou hodnotu) původního objektu.  
  
 .NET Framework automaticky podporuje následující převody:  
  
- Konverze z odvozené třídy na základní třídu. To znamená, že například instance libovolné třídy nebo struktury může být převedena na <xref:System.Object> instanci.  Tento převod nevyžaduje operátor přetypování nebo převodu.  
  
- Konverze ze základní třídy zpět na původní odvozenou třídu. V jazyce C# tento převod vyžaduje operátor přetypování. V Visual Basic vyžaduje `CType` operátor, pokud `Option Strict` je zapnut.  
  
- Převod z typu, který implementuje rozhraní k objektu rozhraní, které představuje toto rozhraní. Tento převod nevyžaduje operátor přetypování nebo převodu.  
  
- Konverze z objektu rozhraní zpět na původní typ, který implementuje toto rozhraní.  V jazyce C# tento převod vyžaduje operátor přetypování. V Visual Basic vyžaduje `CType` operátor, pokud `Option Strict` je zapnut.  
  
 Kromě těchto automatických převodů .NET Framework poskytuje několik funkcí, které podporují převod vlastního typu. Patří mezi ně například:  
  
- `Implicit`Operátor, který definuje dostupné rozšiřující převody mezi typy. Další informace naleznete v části [implicitní převod s implicitním operátorem](#implicit-conversion-with-the-implicit-operator) .  
  
- `Explicit`Operátor, který definuje dostupné zužující převody mezi typy. Další informace naleznete v části [explicitní převod s explicitním operátorem](#explicit-conversion-with-the-explicit-operator) .  
  
- <xref:System.IConvertible>Rozhraní, které definuje převody na jednotlivé základní .NET Framework datové typy. Další informace najdete v části [rozhraní IConvertible](#the-iconvertible-interface) .  
  
- <xref:System.Convert>Třída, která poskytuje sadu metod, které implementují metody v <xref:System.IConvertible> rozhraní. Další informace naleznete v oddílu [třída Convert](#the-convert-class) .  
  
- <xref:System.ComponentModel.TypeConverter>Třída, která je základní třídou, která se dá rozšířit tak, aby podporovala převod zadaného typu na jiný typ. Další informace naleznete v oddílu [třídy TypeConverter](#the-typeconverter-class) .  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Implicitní převod s implicitním operátorem  
 Rozšiřující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, který má buď více omezený rozsah, nebo více omezený seznam členů než cílový typ. Rozšiřující převody nemohou způsobit ztrátu dat (ačkoliv mohou způsobit ztrátu přesnosti). Vzhledem k tomu, že nemůže dojít ke ztrátě dat, mohou kompilátory zpracovat převod implicitně nebo transparentně, aniž by bylo nutné použít metodu explicitního převodu nebo operátor přetypování.  
  
> [!NOTE]
> Ačkoli kód, který provede implicitní převod, může volat metodu převodu nebo použít operátor přetypování, není jejich používání vyžadováno kompilátory, které podporují implicitní převody.  
  
 Například <xref:System.Decimal> Typ podporuje implicitní převody z <xref:System.Byte> <xref:System.Char> hodnot,, <xref:System.Int16> , <xref:System.Int32> , <xref:System.Int64> , <xref:System.SByte> , <xref:System.UInt16> , <xref:System.UInt32> a <xref:System.UInt64> . Následující příklad ilustruje některé z těchto implicitních převodů při přiřazování hodnot <xref:System.Decimal> proměnné.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Pokud kompilátor určitého jazyka podporuje vlastní operátory, můžete ve vlastních typech definovat také implicitní převody. Následující příklad poskytuje částečnou implementaci podepsaného bajtového datového typu s názvem `ByteWithSign` , který používá reprezentaci se znaménkem a velikostí. Podporuje implicitní převod <xref:System.Byte> <xref:System.SByte> hodnot a na `ByteWithSign` hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Kód klienta pak může deklarovat `ByteWithSign` proměnnou a přiřadit ji <xref:System.Byte> a <xref:System.SByte> hodnoty bez provedení explicitních převodů nebo pomocí operátorů přetypování, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Explicitní převod s explicitním operátorem  
 Zužující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, která má buď větší rozsah, nebo větší seznam členů než cílový typ. Vzhledem k tomu, že zužující převod může mít za následek ztrátu dat, kompilátory často vyžadují, aby byl převod vytvořen explicitně prostřednictvím volání metody převodu nebo operátoru přetypování. To znamená, že převod musí být zpracován explicitně v kódu vývojáře.  
  
> [!NOTE]
> Hlavní účel, který vyžaduje metodu převodu nebo operátor přetypování pro zužující převody, je poskytnout vývojářům možnost, že může dojít ke ztrátě dat nebo k <xref:System.OverflowException> tomu, aby mohla být zpracována v kódu. Některé kompilátory však mohou tento požadavek zmírnit. Například pokud je v Visual Basic `Option Strict` vypnuto (výchozí nastavení), Visual Basic kompilátor se pokusí provést zužující převody implicitně.  
  
 Například <xref:System.UInt32> <xref:System.Int64> <xref:System.UInt64> datové typy, a mají rozsahy, které překračují <xref:System.Int32> datový typ, jak je uvedeno v následující tabulce.  
  
|Typ|Porovnání s rozsahem Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType> a <xref:System.Int64.MinValue?displayProperty=nameWithType> je menší než (má větší záporný rozsah než) <xref:System.Int32.MinValue?displayProperty=nameWithType> .|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType> .|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType> .|  
  
 Pro zpracování těchto zužujících převodů .NET Framework umožňuje typům definovat `Explicit` operátor. Kompilátory jednotlivých jazyků mohou následně implementovat tento operátor pomocí vlastní syntaxe, nebo <xref:System.Convert> může být volána člen třídy k provedení převodu. (Další informace o <xref:System.Convert> třídě naleznete v části [třída Convert](#the-convert-class) dále v tomto tématu.) Následující příklad znázorňuje použití funkcí jazyka pro zpracování explicitního převodu těchto potenciálně celočíselných hodnot z rozsahu na <xref:System.Int32> hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Explicitní převody mohou mít různé výsledky v různých jazycích a tyto výsledky se mohou lišit od hodnoty vrácené odpovídající <xref:System.Convert> metodou. Například pokud <xref:System.Double> je hodnota 12,63251 převedena na <xref:System.Int32> , jak metoda Visual Basic, tak `CInt` <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> metoda .NET Framework zaokrouhlí, <xref:System.Double> aby vracela hodnotu 13, ale operátor jazyka C# `(int)` zkrátí a <xref:System.Double> vrátí hodnotu 12. Podobně operátor jazyka C# `(int)` nepodporuje převod Boolean-to-Integer, ale `CInt` Metoda Visual Basic převede hodnotu `true` na-1. Na druhé straně <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> Metoda převede hodnotu `true` na 1.  
  
 Většina kompilátorů umožňuje, aby explicitní převody byly prováděny zkontrolovaným, nebo nezkontrolovaným způsobem. Je-li proveden kontrolovaný převod, <xref:System.OverflowException> je vyvolána, pokud hodnota typu, který má být převeden, je mimo rozsah cílového typu. Pokud je nezkontrolovaný převod proveden za stejných podmínek, nemusí převod vyvolat výjimku, ale stejné chování bude nedefinováno a může mít za následek nesprávnou hodnotu.  
  
> [!NOTE]
> V jazyce C# lze zaškrtnuté převody provádět pomocí `checked` klíčového slova spolu s operátorem přetypování, nebo zadáním `/checked+` Možnosti kompilátoru. Naopak nekontrolované převody lze provádět pomocí `unchecked` klíčového slova spolu s operátorem přetypování, nebo zadáním `/checked-` Možnosti kompilátoru. Ve výchozím nastavení jsou explicitní převody nezkontrolované. V Visual Basic lze provést zaškrtnuté převody zaškrtnutím políčka **Odebrat kontroly přetečení celých čísel** v dialogovém okně **Pokročilé nastavení kompilátoru** projektu nebo zadáním `/removeintchecks-` Možnosti kompilátoru. Naopak nezaškrtnuté převody lze provést zaškrtnutím políčka **Odebrat kontroly přetečení celých čísel** v dialogovém okně **Pokročilé nastavení kompilátoru** projektu nebo zadáním `/removeintchecks+` Možnosti kompilátoru. Ve výchozím nastavení jsou explicitní převody zkontrolované.  
  
 Následující příklad jazyka C# používá `checked` `unchecked` klíčová slova a k ilustraci rozdílu v chování, pokud je hodnota mimo rozsah a <xref:System.Byte> převedena na <xref:System.Byte> . Kontrolovaný převod vyvolá výjimku, ale nekontrolovaný převod přiřadí <xref:System.Byte.MaxValue?displayProperty=nameWithType> <xref:System.Byte> proměnné.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Pokud konkrétní jazykový kompilátor podporuje vlastní přetížené operátory, můžete ve vlastních typech definovat také explicitní převody. Následující příklad poskytuje částečnou implementaci podepsaného bajtového datového typu s názvem `ByteWithSign` , který používá reprezentaci se znaménkem a velikostí. Podporuje explicitní převod <xref:System.Int32> <xref:System.UInt32> hodnot a na `ByteWithSign` hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Klientský kód pak může deklarovat `ByteWithSign` proměnnou a přiřadit ji <xref:System.Int32> a <xref:System.UInt32> hodnoty, pokud přiřazení zahrnují operátor přetypování nebo metodu převodu, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>Rozhraní IConvertible  
 Pro podporu převodu libovolného typu na základní typ modulu CLR je .NET Framework poskytovat <xref:System.IConvertible> rozhraní. Implementující typ je vyžadován pro následující akce:  
  
- Metoda, která vrátí <xref:System.TypeCode> implementující typ.  
  
- Metody pro převod implementující typu na každý základní typ modulu CLR ( <xref:System.Boolean> , <xref:System.Byte> , <xref:System.DateTime> , <xref:System.Decimal> , <xref:System.Double> a tak dále).  
  
- Zobecněná metoda převodu k převedení instance implementujícího typu na jiný určený typ. Převody, které nejsou podporovány, by měly vyvolat <xref:System.InvalidCastException> .  
  
 Každý základní typ modulu CLR (to znamená,,,,, <xref:System.Boolean> <xref:System.Byte> <xref:System.Char> <xref:System.DateTime> <xref:System.Decimal> <xref:System.Double> , <xref:System.Int16> , <xref:System.Int32> , <xref:System.Int64> , <xref:System.SByte> , <xref:System.Single> , <xref:System.String> , <xref:System.UInt16> , <xref:System.UInt32> , a <xref:System.UInt64> ) <xref:System.DBNull> a také <xref:System.Enum> typy a implementují <xref:System.IConvertible> rozhraní. Jedná se však o explicitní implementace rozhraní; metodu převodu lze volat pouze prostřednictvím <xref:System.IConvertible> proměnné rozhraní, jak ukazuje následující příklad. Tento příklad převede <xref:System.Int32> hodnotu na odpovídající <xref:System.Char> hodnotu.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Pokud je požadavek volání metody převodu uplatněn na rozhraní a nikoli na implementující typ, jsou implementace explicitního rozhraní poměrně nákladné. Místo toho doporučujeme, abyste volali příslušného člena <xref:System.Convert> třídy pro převod mezi základními typy modulu CLR (Common Language Runtime). Další informace naleznete v další části [třídy Convert](#the-convert-class).  
  
> [!NOTE]
> Kromě <xref:System.IConvertible> rozhraní a <xref:System.Convert> třídy poskytované .NET Framework mohou jednotlivé jazyky také poskytovat způsoby provádění převodů. Například jazyk C# používá operátory přetypování; Visual Basic používá funkce převodu implementované kompilátorem, jako jsou `CType` , `CInt` a `DirectCast` .  
  
 Ve většině případů <xref:System.IConvertible> je rozhraní navrženo tak, aby podporovalo převod mezi základními typy v .NET Framework. Rozhraní lze však implementovat také pomocí vlastního typu, a podpořit tak převod tohoto typu na vlastní typy. Další informace najdete v části [vlastní převody s metodou ChangeType](#custom-conversions-with-the-changetype-method) dále v tomto tématu.

## <a name="the-convert-class"></a>Třída Convert
 Ačkoliv implementaci rozhraní jednotlivých základních typů <xref:System.IConvertible> lze volat pro provedení převodu typu, volání metod <xref:System.Convert?displayProperty=nameWithType> třídy je doporučeným jazykově neutrálním způsobem pro převod z jednoho základního typu na jiný. Kromě toho <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lze metodu použít k převodu ze zadaného vlastního typu na jiný typ.  
  
### <a name="conversions-between-base-types"></a>Převody mezi základními typy  
 <xref:System.Convert>Třída poskytuje jazykově neutrální způsob pro provádění převodů mezi základními typy a je k dispozici pro všechny jazyky, které cílí na modul CLR (Common Language Runtime). Poskytuje kompletní sadu metod pro rozšiřující i zúžené převody a vyvolá <xref:System.InvalidCastException> pro převody, které nejsou podporovány (například převod <xref:System.DateTime> hodnoty na celočíselnou hodnotu). Zužující převody jsou prováděny v kontrolovaném kontextu a <xref:System.OverflowException> vyvolá se v případě, že převod se nezdařil.  
  
> [!IMPORTANT]
> Vzhledem k tomu, že <xref:System.Convert> Třída obsahuje metody pro převod na a z každého základního typu, eliminuje nutnost volat <xref:System.IConvertible> explicitní implementaci rozhraní jednotlivých základních typů.  
  
 Následující příklad ilustruje použití <xref:System.Convert?displayProperty=nameWithType> třídy k provedení několika rozšiřujících a zužujících převodů mezi .NET Framework základními typy.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 V některých případech, zejména při převodu do a z hodnot s plovoucí desetinnou čárkou, může převod zahrnovat ztrátu přesnosti, i když nevyvolá <xref:System.OverflowException> . Následující příklad znázorňuje tuto ztrátu přesnosti. V prvním případě <xref:System.Decimal> má hodnota menší přesnost (méně platných číslic), když je převedena na <xref:System.Double> . Ve druhém případě <xref:System.Double> je hodnota zaokrouhlena z 42,72 na 43, aby bylo možné dokončit převod.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Tabulku, která obsahuje seznam rozšiřujících a zužujících převodů, které jsou podporovány <xref:System.Convert> třídou, naleznete v tématu [převodní tabulky typů](conversion-tables.md).  

### <a name="custom-conversions-with-the-changetype-method"></a>Vlastní převody pomocí metody ChangeType  
 Kromě podpory převodů na jednotlivé základní typy <xref:System.Convert> lze třídu použít k převedení vlastního typu na jeden nebo více předdefinovaných typů. Tento převod provádí <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metoda, která zase zabalí volání <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> metody `value` parametru. To znamená, že objekt reprezentovaný `value` parametrem musí poskytovat implementaci <xref:System.IConvertible> rozhraní.  
  
> [!NOTE]
> Vzhledem k <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> tomu <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> , že metody a používají <xref:System.Type> objekt k určení cílového typu `value` , který je převeden, lze použít k provedení dynamického převodu na objekt, jehož typ není v době kompilace znám. Nicméně Všimněte si, že <xref:System.IConvertible> implementace `value` musí stále podporovat tento převod.  
  
 Následující příklad ilustruje možnou implementaci <xref:System.IConvertible> rozhraní, které umožňuje `TemperatureCelsius` převést objekt na `TemperatureFahrenheit` objekt a naopak. Příklad definuje základní třídu, `Temperature` , která implementuje <xref:System.IConvertible> rozhraní a Přepisuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu. Odvozené `TemperatureCelsius` třídy a `TemperatureFahrenheit` třídy přepíší `ToType` a `ToString` metody základní třídy.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Následující příklad znázorňuje několik volání těchto <xref:System.IConvertible> implementací pro převod `TemperatureCelsius` objektů na `TemperatureFahrenheit` objekty a naopak.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>Třída TypeConverter  
 .NET Framework také umožňuje definovat konvertor typu pro vlastní typ rozšířením <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> třídy a přidružením konvertoru typu k typu prostřednictvím <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> atributu. Následující tabulka popisuje rozdíly mezi tímto přístupem a implementací <xref:System.IConvertible> rozhraní pro vlastní typ.  
  
> [!NOTE]
> Podporu v době návrhu lze pro vlastní typ zajistit pouze tehdy, pokud byl definován konvertor typu.  
  
|Převod pomocí TypeConverter|Převod pomocí IConvertible|  
|------------------------------------|-----------------------------------|  
|Je implementován pro vlastní typ odvozením samostatné třídy z <xref:System.ComponentModel.TypeConverter> . Tato odvozená třída je přidružená k vlastnímu typu použitím <xref:System.ComponentModel.TypeConverterAttribute> atributu.|Je implementován vlastním typem za účelem převodu. Uživatel typu vyvolá <xref:System.IConvertible> metodu převodu pro typ.|  
|Lze použít v době návrhu i v době spuštění.|Lze použít pouze v době spuštění.|  
|Používá reflexi; Proto je pomalejší než Převod povolený pomocí <xref:System.IConvertible> .|Nepoužívá reflexi.|  
|Umožňuje obousměrný převod typu z vlastního typu na jiné datové typy a z jiných datových typů na vlastní typ. Například <xref:System.ComponentModel.TypeConverter> definice pro `MyType` umožňuje převod z `MyType` na a <xref:System.String> z <xref:System.String> na `MyType` .|Umožňuje převod z vlastního typu na jiné datové typy, nikoli však z jiných datových typů na vlastní typ.|  
  
 Další informace o použití převaděčů typů pro provádění převodů naleznete v tématu <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tabulky převodu typů](conversion-tables.md)
