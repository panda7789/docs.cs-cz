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
ms.openlocfilehash: b125b3c6527da405deb600ba7334ef18220f1601
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132871"
---
# <a name="type-conversion-in-the-net-framework"></a>Převod typů v rozhraní .NET Framework
<a name="top"></a>Každá hodnota má přidružený typ, který definuje atributy, jako je například množství prostoru přiděleného hodnotě, rozsah možných hodnot, které může mít, a členy, které zpřístupňují. Mnoho hodnot lze vyjádřit ve formě více než jednoho typu. Například hodnotu 4 lze vyjádřit jako celé číslo nebo jako hodnotu s plovoucí desetinnou čárkou. Převod typu vytvoří hodnotu v novém typu, která je ekvivalentní hodnotě starého typu, ale nutně nezachová identitu (nebo přesnou hodnotu) původního objektu.  
  
 .NET Framework automaticky podporuje následující převody:  
  
- Konverze z odvozené třídy na základní třídu. To znamená, že například instance libovolné třídy nebo struktury může být převedena na instanci <xref:System.Object>.  Tento převod nevyžaduje operátor přetypování nebo převodu.  
  
- Konverze ze základní třídy zpět na původní odvozenou třídu. V C#, tento převod vyžaduje operátor přetypování. V Visual Basic vyžaduje, aby byl operátor `CType`, pokud je `Option Strict` zapnutý.  
  
- Převod z typu, který implementuje rozhraní k objektu rozhraní, které představuje toto rozhraní. Tento převod nevyžaduje operátor přetypování nebo převodu.  
  
- Konverze z objektu rozhraní zpět na původní typ, který implementuje toto rozhraní.  V C#, tento převod vyžaduje operátor přetypování. V Visual Basic vyžaduje, aby byl operátor `CType`, pokud je `Option Strict` zapnutý.  
  
 Kromě těchto automatických převodů .NET Framework poskytuje několik funkcí, které podporují převod vlastního typu. Patří mezi ně například:  
  
- Operátor `Implicit`, který definuje dostupné rozšiřující převody mezi typy. Další informace naleznete v části [implicitní převod s implicitním operátorem](#implicit_conversion_with_the_implicit_operator) .  
  
- Operátor `Explicit`, který definuje dostupné zužující převody mezi typy. Další informace naleznete v části [explicitní převod s explicitním operátorem](#explicit_conversion_with_the_explicit_operator) .  
  
- Rozhraní <xref:System.IConvertible>, které definuje převody na jednotlivé základní .NET Framework datové typy. Další informace najdete v části [rozhraní IConvertible](#the_iconvertible_interface) .  
  
- Třída <xref:System.Convert>, která poskytuje sadu metod, které implementují metody v rozhraní <xref:System.IConvertible>. Další informace naleznete v oddílu [třída Convert](#Convert) .  
  
- Třída <xref:System.ComponentModel.TypeConverter>, která je základní třídou, která se dá rozšířit tak, aby podporovala převod zadaného typu na jakýkoliv jiný typ. Další informace naleznete v oddílu [třídy TypeConverter](#the_typeconverter_class) .  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Implicitní převod s implicitním operátorem  
 Rozšiřující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, který má buď více omezený rozsah, nebo více omezený seznam členů než cílový typ. Rozšiřující převody nemohou způsobit ztrátu dat (ačkoliv mohou způsobit ztrátu přesnosti). Vzhledem k tomu, že nemůže dojít ke ztrátě dat, mohou kompilátory zpracovat převod implicitně nebo transparentně, aniž by bylo nutné použít metodu explicitního převodu nebo operátor přetypování.  
  
> [!NOTE]
> Ačkoli kód, který provede implicitní převod, může volat metodu převodu nebo použít operátor přetypování, není jejich používání vyžadováno kompilátory, které podporují implicitní převody.  
  
 Například typ <xref:System.Decimal> podporuje implicitní převody z <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>a <xref:System.UInt64> hodnot. Následující příklad ilustruje některé z těchto implicitních převodů při přiřazování hodnot proměnné <xref:System.Decimal>.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Pokud kompilátor určitého jazyka podporuje vlastní operátory, můžete ve vlastních typech definovat také implicitní převody. Následující příklad poskytuje částečnou implementaci datového typu se znaménkem v bajtu s názvem `ByteWithSign`, který používá reprezentaci se znaménkem a velikostí. Podporuje implicitní převod hodnot <xref:System.Byte> a <xref:System.SByte> na hodnoty `ByteWithSign`.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Klientský kód pak může deklarovat `ByteWithSign` proměnnou a přiřadit jí <xref:System.Byte> a <xref:System.SByte> hodnoty bez provedení explicitních převodů nebo pomocí operátorů přetypování, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Zpět na začátek](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Explicitní převod s explicitním operátorem  
 Zužující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, která má buď větší rozsah, nebo větší seznam členů než cílový typ. Vzhledem k tomu, že zužující převod může mít za následek ztrátu dat, kompilátory často vyžadují, aby byl převod vytvořen explicitně prostřednictvím volání metody převodu nebo operátoru přetypování. To znamená, že převod musí být zpracován explicitně v kódu vývojáře.  
  
> [!NOTE]
> Hlavní účel, který vyžaduje metodu převodu nebo operátor přetypování pro zužující převody, je poskytnout vývojářům možnost, že může dojít ke ztrátě dat nebo <xref:System.OverflowException>, aby mohla být zpracována v kódu. Některé kompilátory však mohou tento požadavek zmírnit. Například v Visual Basic, pokud je `Option Strict` vypnutá (výchozí nastavení), kompilátor Visual Basic se pokusí provést zužující převody implicitně.  
  
 Například datové typy <xref:System.UInt32>, <xref:System.Int64>a <xref:System.UInt64> mají rozsahy, které překračují datový typ <xref:System.Int32>, jak je uvedeno v následující tabulce.  
  
|Typ|Porovnání s rozsahem Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>a <xref:System.Int64.MinValue?displayProperty=nameWithType> je menší než (má větší záporný rozsah než) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Pro zpracování těchto zužujících převodů .NET Framework umožňuje typům definovat operátor `Explicit`. Kompilátory jednotlivých jazyků mohou následně implementovat tento operátor pomocí vlastní syntaxe, nebo může být volána člen třídy <xref:System.Convert> k provedení převodu. (Další informace o třídě <xref:System.Convert> naleznete dále v tomto tématu v [třídě Convert](#Convert) .) Následující příklad znázorňuje použití funkcí jazyka pro zpracování explicitního převodu těchto potenciálně celočíselných hodnot z rozsahu na <xref:System.Int32> hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Explicitní převody mohou mít různé výsledky v různých jazycích a tyto výsledky se mohou lišit od hodnoty vrácené odpovídající <xref:System.Convert> metodou. Pokud je například hodnota <xref:System.Double> 12,63251 převedena na <xref:System.Int32>, metoda Visual Basic `CInt` i metoda .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> zaokrouhlí <xref:System.Double>, aby vrátilo hodnotu 13, ale operátor C# `(int)` zkrátí <xref:System.Double> na Vrátí hodnotu 12. Podobně operátor C# `(int)` nepodporuje převod Boolean-to-Integer, ale metoda `CInt` Visual Basic převádí hodnotu `true` na-1. Na druhé straně <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> metoda převede hodnotu `true` na 1.  
  
 Většina kompilátorů umožňuje, aby explicitní převody byly prováděny zkontrolovaným, nebo nezkontrolovaným způsobem. Při provedení kontrolovaného převodu je vyvolána <xref:System.OverflowException>, když hodnota typu, který má být převeden, je mimo rozsah cílového typu. Pokud je nezkontrolovaný převod proveden za stejných podmínek, nemusí převod vyvolat výjimku, ale stejné chování bude nedefinováno a může mít za následek nesprávnou hodnotu.  
  
> [!NOTE]
> V C#lze kontrolované převody provádět pomocí klíčového slova `checked` spolu s operátorem přetypování, nebo zadáním možnosti kompilátoru `/checked+`. Naopak nekontrolované převody lze provádět pomocí klíčového slova `unchecked` spolu s operátorem přetypování, nebo zadáním možnosti kompilátoru `/checked-`. Ve výchozím nastavení jsou explicitní převody nezkontrolované. V Visual Basic lze kontrolované převody provést zrušením zaškrtnutí políčka **Odebrat kontroly přetečení celých čísel** v dialogovém okně **Pokročilé nastavení kompilátoru** projektu nebo zadáním možnosti kompilátoru `/removeintchecks-`. Naopak nezaškrtnuté převody lze provést zaškrtnutím políčka **Odebrat kontroly přetečení celých čísel** v dialogovém okně **Pokročilé nastavení kompilátoru** projektu nebo zadáním možnosti kompilátoru `/removeintchecks+`. Ve výchozím nastavení jsou explicitní převody zkontrolované.  
  
 Následující C# příklad používá klíčová slova `checked` a `unchecked` k ilustraci rozdílu v chování, pokud je hodnota mimo rozsah <xref:System.Byte> převedena na <xref:System.Byte>. Kontrolovaný převod vyvolá výjimku, ale nekontrolovaný převod přiřadí <xref:System.Byte.MaxValue?displayProperty=nameWithType> k proměnné <xref:System.Byte>.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Pokud konkrétní jazykový kompilátor podporuje vlastní přetížené operátory, můžete ve vlastních typech definovat také explicitní převody. Následující příklad poskytuje částečnou implementaci datového typu se znaménkem v bajtu s názvem `ByteWithSign`, který používá reprezentaci se znaménkem a velikostí. Podporuje explicitní převod hodnot <xref:System.Int32> a <xref:System.UInt32> na hodnoty `ByteWithSign`.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Klientský kód pak může deklarovat `ByteWithSign` proměnnou a přiřadit <xref:System.Int32> a <xref:System.UInt32> hodnoty, pokud přiřazení zahrnují operátor přetypování nebo metodu převodu, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>Rozhraní IConvertible  
 Aby bylo možné podporovat převod jakéhokoli typu na základní typ modulu CLR, .NET Framework poskytuje rozhraní <xref:System.IConvertible>. Implementující typ je vyžadován pro následující akce:  
  
- Metoda, která vrací <xref:System.TypeCode> implementující typu.  
  
- Metody pro převod implementující typu na každý základní typ modulu CLR (Common Language Runtime) (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>a tak dále).  
  
- Zobecněná metoda převodu k převedení instance implementujícího typu na jiný určený typ. Převody, které nejsou podporovány, by měly vyvolat <xref:System.InvalidCastException>.  
  
 Každý základní typ modulu CLR (Common Language Runtime) (to znamená <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>a <xref:System.UInt64>), stejně jako <xref:System.DBNull> a <xref:System.Enum> typy, implementujte rozhraní <xref:System.IConvertible>. Jedná se však o explicitní implementace rozhraní; metodu převodu lze volat pouze prostřednictvím proměnné rozhraní <xref:System.IConvertible>, jak ukazuje následující příklad. Tento příklad převede hodnotu <xref:System.Int32> na ekvivalentní <xref:System.Char> hodnotu.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Pokud je požadavek volání metody převodu uplatněn na rozhraní a nikoli na implementující typ, jsou implementace explicitního rozhraní poměrně nákladné. Místo toho doporučujeme volat příslušný člen třídy <xref:System.Convert> pro převod mezi základními typy modulu CLR (Common Language Runtime). Další informace naleznete v další části [třídy Convert](#Convert).  
  
> [!NOTE]
> Kromě rozhraní <xref:System.IConvertible> a <xref:System.Convert> třídy poskytované .NET Framework mohou jednotlivé jazyky také poskytovat způsoby provádění převodů. Například C# používá operátory přetypování; Visual Basic používá funkce převodu implementované kompilátorem, jako jsou `CType`, `CInt`a `DirectCast`.  
  
 Ve většině případů je rozhraní <xref:System.IConvertible> navrženo tak, aby podporovalo převod mezi základními typy v .NET Framework. Rozhraní lze však implementovat také pomocí vlastního typu, a podpořit tak převod tohoto typu na vlastní typy. Další informace najdete v části [vlastní převody s metodou ChangeType](#ChangeType) dále v tomto tématu.  
  
 [Zpět na začátek](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Třída Convert  
 I když je možné volat jednotlivé implementace rozhraní <xref:System.IConvertible> rozhraní, aby se prováděl převod typu, volání metod třídy <xref:System.Convert?displayProperty=nameWithType> je doporučeným jazykově neutrálním způsobem pro převod z jednoho základního typu na jiný. Kromě toho lze metodu <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> použít k převodu ze zadaného vlastního typu na jiný typ.  
  
### <a name="conversions-between-base-types"></a>Převody mezi základními typy  
 Třída <xref:System.Convert> poskytuje jazykově neutrální způsob pro provádění převodů mezi základními typy a je k dispozici pro všechny jazyky, které cílí na modul CLR (Common Language Runtime). Poskytuje kompletní sadu metod pro rozšiřující i zužující převody a vyvolá <xref:System.InvalidCastException> pro převody, které nejsou podporovány (například převod <xref:System.DateTime> hodnoty na celočíselnou hodnotu). Zužující převody jsou prováděny v kontrolovaném kontextu a <xref:System.OverflowException> je vyvolána, pokud se převod nezdařil.  
  
> [!IMPORTANT]
> Vzhledem k tomu, že třída <xref:System.Convert> obsahuje metody pro převod na a z každého základního typu, eliminuje nutnost volání <xref:System.IConvertible> explicitní implementace rozhraní pro jednotlivé základní typy.  
  
 Následující příklad ilustruje použití třídy <xref:System.Convert?displayProperty=nameWithType> k provedení několika rozšiřujících a zužujících převodů mezi .NET Framework základními typy.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 V některých případech, zejména při převodu do a z hodnot s plovoucí desetinnou čárkou, může převod zahrnovat ztrátu přesnosti, i když nevyvolá <xref:System.OverflowException>. Následující příklad znázorňuje tuto ztrátu přesnosti. V prvním případě má hodnota <xref:System.Decimal> menší přesnost (méně platných číslic), když je převedena na <xref:System.Double>. V druhém případě je hodnota <xref:System.Double> zaokrouhlena z 42,72 na 43, aby bylo možné dokončit převod.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Tabulka, která obsahuje seznam rozšiřujících a zužujících převodů podporovaných třídou <xref:System.Convert>, naleznete v tématu [převodní tabulky typů](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>Vlastní převody pomocí metody ChangeType  
 Kromě podpory převodů na jednotlivé základní typy lze třídu <xref:System.Convert> použít k převedení vlastního typu na jeden nebo více předdefinovaných typů. Tento převod provádí metoda <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, která zase zabalí volání metody <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> parametru `value`. To znamená, že objekt reprezentovaný parametrem `value` musí poskytovat implementaci rozhraní <xref:System.IConvertible>.  
  
> [!NOTE]
> Vzhledem k tomu, že metody <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> a <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> používají objekt <xref:System.Type> k určení cílového typu, ke kterému je `value` převeden, lze použít k provedení dynamického převodu na objekt, jehož typ není znám v době kompilace. Upozorňujeme však, že <xref:System.IConvertible> implementace `value` musí nadále podporovat tento převod.  
  
 Následující příklad znázorňuje možnou implementaci rozhraní <xref:System.IConvertible>, která umožňuje převést objekt `TemperatureCelsius` na objekt `TemperatureFahrenheit` a naopak. Příklad definuje základní třídu, `Temperature`, která implementuje rozhraní <xref:System.IConvertible> a přepisuje metodu <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Odvozené třídy `TemperatureCelsius` a `TemperatureFahrenheit` přepíší `ToType` a metody `ToString` základní třídy.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Následující příklad znázorňuje několik volání těchto <xref:System.IConvertible> implementace k převedení `TemperatureCelsius` objektů na `TemperatureFahrenheit` objektů a naopak.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>Třída TypeConverter  
 .NET Framework také umožňuje definovat konvertor typu pro vlastní typ rozšířením třídy <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> a přidružením konvertoru typu k typu prostřednictvím atributu <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType>. Následující tabulka popisuje rozdíly mezi tímto přístupem a implementací rozhraní <xref:System.IConvertible> pro vlastní typ.  
  
> [!NOTE]
> Podporu v době návrhu lze pro vlastní typ zajistit pouze tehdy, pokud byl definován konvertor typu.  
  
|Převod pomocí TypeConverter|Převod pomocí IConvertible|  
|------------------------------------|-----------------------------------|  
|Je implementován pro vlastní typ odvozením samostatné třídy z <xref:System.ComponentModel.TypeConverter>. Tato odvozená třída je přidružená k vlastnímu typu použitím atributu <xref:System.ComponentModel.TypeConverterAttribute>.|Je implementován vlastním typem za účelem převodu. Uživatel typu vyvolá metodu převodu <xref:System.IConvertible> pro daný typ.|  
|Lze použít v době návrhu i v době spuštění.|Lze použít pouze v době spuštění.|  
|Používá reflexi; Proto je pomalejší než Převod povolený pomocí <xref:System.IConvertible>.|Nepoužívá reflexi.|  
|Umožňuje obousměrný převod typu z vlastního typu na jiné datové typy a z jiných datových typů na vlastní typ. Například <xref:System.ComponentModel.TypeConverter> definovaná pro `MyType` umožňuje převody z `MyType` na <xref:System.String>a z <xref:System.String> na `MyType`.|Umožňuje převod z vlastního typu na jiné datové typy, nikoli však z jiných datových typů na vlastní typ.|  
  
 Další informace o použití převaděčů typů pro provádění převodů naleznete v tématu <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tabulky převodu typů](../../../docs/standard/base-types/conversion-tables.md)
