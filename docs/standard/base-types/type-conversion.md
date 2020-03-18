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
ms.openlocfilehash: 0e88303f2bac2dae90a97f9d2de92af1d2a0f80d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976494"
---
# <a name="type-conversion-in-the-net-framework"></a>Převod typů v rozhraní .NET Framework
Každá hodnota má přidružený typ, který definuje atributy, jako je například velikost místa přiděleného hodnotě, rozsah možných hodnot, které může mít, a členy, které zpřístupní. Mnoho hodnot lze vyjádřit ve formě více než jednoho typu. Například hodnotu 4 lze vyjádřit jako celé číslo nebo jako hodnotu s plovoucí desetinnou čárkou. Převod typu vytvoří hodnotu v novém typu, která je ekvivalentní hodnotě starého typu, ale nutně nezachová identitu (nebo přesnou hodnotu) původního objektu.  
  
 Rozhraní .NET Framework automaticky podporuje následující převody:  
  
- Převod z odvozené třídy na základní třídu. To například znamená, že instanci libovolné třídy nebo <xref:System.Object> struktury lze převést na instanci.  Tento převod nevyžaduje operátor přetypování nebo převodu.  
  
- Převod ze základní třídy zpět na původní odvozené třídy. V c#, tento převod vyžaduje operátor přetypování. V jazyce Visual `CType` Basic `Option Strict` vyžaduje operátor, pokud je zapnuto.  
  
- Převod z typu, který implementuje rozhraní na objekt rozhraní, který představuje toto rozhraní. Tento převod nevyžaduje operátor přetypování nebo převodu.  
  
- Převod z objektu rozhraní zpět na původní typ, který implementuje toto rozhraní.  V c#, tento převod vyžaduje operátor přetypování. V jazyce Visual `CType` Basic `Option Strict` vyžaduje operátor, pokud je zapnuto.  
  
 Kromě těchto automatických převodů poskytuje rozhraní .NET Framework několik funkcí, které podporují převod vlastního typu. Patří mezi ně například:  
  
- Operátor, `Implicit` který definuje dostupné rozšiřující převody mezi typy. Další informace naleznete [v části Implicitní převod s implicitním operátorem.](#implicit-conversion-with-the-implicit-operator)  
  
- Operátor, `Explicit` který definuje dostupné zužující převody mezi typy. Další informace naleznete v části [Explicitní převod s explicitním operátorem.](#explicit-conversion-with-the-explicit-operator)  
  
- Rozhraní, <xref:System.IConvertible> které definuje převody na každý z datových typů základní rozhraní .NET Framework. Další informace naleznete v části [Rozhraní IKonslete.](#the-iconvertible-interface)  
  
- Třída, <xref:System.Convert> která poskytuje sadu metod, které implementují metody v <xref:System.IConvertible> rozhraní. Další informace naleznete v části [Převést třídu.](#the-convert-class)  
  
- Třída, <xref:System.ComponentModel.TypeConverter> což je základní třída, která může být rozšířena tak, aby podporovala převod zadaného typu na jiný typ. Další informace naleznete v části [Třída převaděče typeconverteru.](#the-typeconverter-class)  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Implicitní převod s implicitním operátorem  
 Rozšiřující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, který má buď více omezený rozsah, nebo více omezený seznam členů než cílový typ. Rozšiřující převody nemohou způsobit ztrátu dat (ačkoliv mohou způsobit ztrátu přesnosti). Vzhledem k tomu, že nemůže dojít ke ztrátě dat, mohou kompilátory zpracovat převod implicitně nebo transparentně, aniž by bylo nutné použít metodu explicitního převodu nebo operátor přetypování.  
  
> [!NOTE]
> Ačkoli kód, který provede implicitní převod, může volat metodu převodu nebo použít operátor přetypování, není jejich používání vyžadováno kompilátory, které podporují implicitní převody.  
  
 <xref:System.Decimal> Například typ podporuje implicitní <xref:System.Byte>převody z <xref:System.Int64> <xref:System.SByte>, <xref:System.UInt16> <xref:System.Char> <xref:System.Int16>, <xref:System.Int32> <xref:System.UInt64> , , , <xref:System.UInt32>, a hodnoty. Následující příklad ilustruje některé z těchto implicitních převodů <xref:System.Decimal> při přiřazování hodnot proměnné.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Pokud kompilátor určitého jazyka podporuje vlastní operátory, můžete ve vlastních typech definovat také implicitní převody. Následující příklad obsahuje částečnou implementaci podepsaného bajtového datového typu s názvem, `ByteWithSign` který používá reprezentaci podepisování a velikosti. Podporuje implicitní <xref:System.Byte> převod <xref:System.SByte> a `ByteWithSign` hodnoty na hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Klientský kód pak `ByteWithSign` může deklarovat proměnnou a přiřadit ji <xref:System.Byte> a <xref:System.SByte> hodnoty bez provedení explicitní převody nebo pomocí libovolné hodování operátory, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Explicitní převod s explicitním operátorem  
 Zužující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, která má buď větší rozsah, nebo větší seznam členů než cílový typ. Vzhledem k tomu, že zužující převod může mít za následek ztrátu dat, kompilátory často vyžadují, aby byl převod vytvořen explicitně prostřednictvím volání metody převodu nebo operátoru přetypování. To znamená, že převod musí být zpracován explicitně v kódu vývojáře.  
  
> [!NOTE]
> Hlavním účelem vyžadování metody převodu nebo operátoru přetypování pro zúžení převodů <xref:System.OverflowException> je seznámit vývojáře s možností ztráty dat nebo tak, aby bylo možné s ním zacházet v kódu. Některé kompilátory však mohou tento požadavek zmírnit. Například v jazyce `Option Strict` Visual Basic, pokud je vypnuto (jeho výchozí nastavení), kompilátor jazyka se pokusí provést zužující převody implicitně.  
  
 Například <xref:System.UInt32>, <xref:System.Int64>a <xref:System.UInt64> datové typy mají oblasti, <xref:System.Int32> které překračují datový typ, jak ukazuje následující tabulka.  
  
|Typ|Porovnání s rozsahem Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>je větší <xref:System.Int32.MaxValue?displayProperty=nameWithType>než <xref:System.Int64.MinValue?displayProperty=nameWithType> , a je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType>(má větší negativní rozsah než) .|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>je větší <xref:System.Int32.MaxValue?displayProperty=nameWithType>než .|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>je větší <xref:System.Int32.MaxValue?displayProperty=nameWithType>než .|  
  
 Chcete-li zpracovat takové zužující převody, `Explicit` rozhraní .NET Framework umožňuje typy definovat operátor. Jednotlivé kompilátory jazyka pak můžete implementovat tento operátor <xref:System.Convert> pomocí vlastní syntaxe nebo člen třídy lze volat k provedení převodu. (Další informace o <xref:System.Convert> třídě najdete v [tématu Převést třídy](#the-convert-class) dále v tomto tématu.) Následující příklad ilustruje použití funkcí jazyka pro zpracování explicitní převod těchto potenciálně mimo rozsah <xref:System.Int32> celočíselné hodnoty na hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Explicitní převody mohou vést k různým výsledkům v různých jazycích <xref:System.Convert> a tyto výsledky se mohou lišit od hodnoty vrácené odpovídající metodou. Například pokud <xref:System.Double> hodnota 12.63251 je převeden <xref:System.Int32>na , `CInt` visual basic metoda <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> a .NET Framework metoda <xref:System.Double> zaokrouhlit `(int)` na vrátit hodnotu <xref:System.Double> 13, ale C# operátor zkrátí vrátit hodnotu 12. Podobně operátor C# `(int)` nepodporuje převod boolean-to-celočíselné, ale `CInt` metoda jazyka převede `true` hodnotu na -1. Na druhé straně <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> metoda převede hodnotu `true` na 1.  
  
 Většina kompilátorů umožňuje, aby explicitní převody byly prováděny zkontrolovaným, nebo nezkontrolovaným způsobem. Při provádění zaškrtnutého převodu <xref:System.OverflowException> je vyvolána, když je hodnota typu, který má být převeden, mimo rozsah cílového typu. Pokud je nezkontrolovaný převod proveden za stejných podmínek, nemusí převod vyvolat výjimku, ale stejné chování bude nedefinováno a může mít za následek nesprávnou hodnotu.  
  
> [!NOTE]
> V C# lze zkontrolovat převody pomocí `checked` klíčového slova společně s operátorem `/checked+` přetypování nebo zadáním možnosti kompilátoru. Naopak nekontrolované převody lze provést pomocí `unchecked` klíčového slova společně s operátorem `/checked-` přetypování nebo zadáním možnosti kompilátoru. Ve výchozím nastavení jsou explicitní převody nezkontrolované. V jazyce Visual Basic lze zaškrtnuté převody provést zrušením zaškrtnutí políčka **Odebrat kontroly přetečení celého** `/removeintchecks-` čísla v dialogovém okně Rozšířené nastavení **kompilátoru** projektu nebo zadáním možnosti kompilátoru. Naopak nezaškrtnuté převody lze provést zaškrtnutím políčka **Odebrat kontroly přetečení celého čísla** v dialogovém okně `/removeintchecks+` Rozšířené nastavení **kompilátoru** projektu nebo zadáním možnosti kompilátoru. Ve výchozím nastavení jsou explicitní převody zkontrolované.  
  
 Následující příklad jazyka C# používá klíčová slova `checked` a `unchecked` k ilustraci <xref:System.Byte> rozdílu v <xref:System.Byte>chování při převodu hodnoty mimo rozsah a . Kontrolovaný převod vyvolá výjimku, ale nezaškrtnutý převod <xref:System.Byte.MaxValue?displayProperty=nameWithType> přiřadí <xref:System.Byte> proměnné.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Pokud konkrétní jazykový kompilátor podporuje vlastní přetížené operátory, můžete ve vlastních typech definovat také explicitní převody. Následující příklad obsahuje částečnou implementaci podepsaného bajtového datového typu s názvem, `ByteWithSign` který používá reprezentaci podepisování a velikosti. Podporuje explicitní převod <xref:System.Int32> <xref:System.UInt32> a `ByteWithSign` hodnoty na hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Kód klienta pak `ByteWithSign` může deklarovat proměnnou a přiřadit ji <xref:System.Int32> a <xref:System.UInt32> hodnoty, pokud přiřazení zahrnují operátor přetypování nebo metodu převodu, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>Rozhraní IConvertible  
 Pro podporu převodu libovolného typu na základní typ běžného modulu runtime poskytuje <xref:System.IConvertible> rozhraní rozhraní .NET Framework. Implementující typ je vyžadován pro následující akce:  
  
- Metoda, která <xref:System.TypeCode> vrací implementující typ.  
  
- Metody převodu implementujícího typu na každý základní<xref:System.Boolean> <xref:System.Byte>typ <xref:System.DateTime> <xref:System.Decimal>běžného jazyka runtime ( , , , <xref:System.Double>, a tak dále).  
  
- Zobecněná metoda převodu k převedení instance implementujícího typu na jiný určený typ. Převody, které nejsou podporovány by měl vyvolat <xref:System.InvalidCastException>.  
  
 Každý základní typ běžného modulu <xref:System.Boolean>runtime <xref:System.Char> <xref:System.DateTime>(tj. <xref:System.Int16> <xref:System.Int32>, <xref:System.Int64> <xref:System.SByte> <xref:System.Single> <xref:System.String> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> <xref:System.DBNull> <xref:System.Enum> <xref:System.Decimal> <xref:System.Byte>, <xref:System.Double>, , , , , , , <xref:System.IConvertible> , , a ), a také a typy, implementujte rozhraní. Jedná se však o explicitní implementace rozhraní; metodu převodu lze volat <xref:System.IConvertible> pouze prostřednictvím proměnné rozhraní, jak ukazuje následující příklad. Tento příklad převede <xref:System.Int32> hodnotu <xref:System.Char> na ekvivalentní hodnotu.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Pokud je požadavek volání metody převodu uplatněn na rozhraní a nikoli na implementující typ, jsou implementace explicitního rozhraní poměrně nákladné. Místo toho doporučujeme zavolat příslušného <xref:System.Convert> člena třídy převést mezi základní typy běžného běhu v jazyce. Další informace naleznete v další části [Převést třídy](#the-convert-class).  
  
> [!NOTE]
> Kromě <xref:System.IConvertible> rozhraní a <xref:System.Convert> třídy poskytované rozhraním .NET Framework mohou jednotlivé jazyky také poskytovat způsoby provádění převodů. Například C# používá operátory přetypování; Visual Basic používá funkce převodu `CType`implementované kompilátorem, například , `CInt`a `DirectCast`.  
  
 Z větší části <xref:System.IConvertible> rozhraní je určen pro podporu převodu mezi základní typy v rozhraní .NET Framework. Rozhraní lze však implementovat také pomocí vlastního typu, a podpořit tak převod tohoto typu na vlastní typy. Další informace naleznete v části [Vlastní převody s metodou ChangeType](#custom-conversions-with-the-changetype-method) dále v tomto tématu.

## <a name="the-convert-class"></a>Třída Convert
 Přestože každý základní <xref:System.IConvertible> typ implementace rozhraní lze volat k provedení převodu typu, volání metody <xref:System.Convert?displayProperty=nameWithType> třídy je doporučený jazykově neutrální způsob, jak převést z jednoho základního typu na jiný. Kromě toho <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lze metodu použít k převodu ze zadaného vlastního typu na jiný typ.  
  
### <a name="conversions-between-base-types"></a>Převody mezi základními typy  
 Třída <xref:System.Convert> poskytuje jazykově neutrální způsob provádění převodů mezi základními typy a je k dispozici všem jazykům, které cílí na běžný jazyk runtime. Poskytuje úplnou sadu metod pro rozšíření a zužující převody <xref:System.InvalidCastException> a vyvolá pro převody, které nejsou <xref:System.DateTime> podporovány (například převod hodnoty na celou hodnotu). Zužující převody jsou prováděny v kontrolovaném kontextu a <xref:System.OverflowException> je vyvolána, pokud se nezdaří převodu.  
  
> [!IMPORTANT]
> Vzhledem <xref:System.Convert> k tomu, že třída obsahuje metody pro převod do a z <xref:System.IConvertible> každého základního typu, eliminuje potřebu volat explicitní implementaci rozhraní každého základního typu.  
  
 Následující příklad ilustruje použití <xref:System.Convert?displayProperty=nameWithType> třídy k provedení několika rozšiřujících a zužujících převodů mezi základními typy rozhraní .NET Framework.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 V některých případech, zejména při převodu na a z hodnoty s plovoucí desetinnou tálicí, převod může zahrnovat ztrátu přesnosti, i když nevyvolá <xref:System.OverflowException>. Následující příklad znázorňuje tuto ztrátu přesnosti. V prvním případě <xref:System.Decimal> hodnota má menší přesnost (méně platných číslic) <xref:System.Double>při převodu na . V druhém případě <xref:System.Double> je hodnota zaokrouhlena z 42.72 na 43 za účelem dokončení převodu.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Tabulka se seznamem rozšiřujících i zužujících <xref:System.Convert> převodů podporovaných třídou naleznete v [tématu Typové konverzní tabulky](../../../docs/standard/base-types/conversion-tables.md).  

### <a name="custom-conversions-with-the-changetype-method"></a>Vlastní převody pomocí metody ChangeType  
 Kromě podpory převody na každý základní typy, <xref:System.Convert> třídy lze převést vlastní typ na jeden nebo více předdefinovaných typů. Tento převod se <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> provádí metodou, která zase zabalí <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> volání `value` metody parametru. To znamená, že objekt `value` reprezentované <xref:System.IConvertible> parametr musí poskytnout implementaci rozhraní.  
  
> [!NOTE]
> Vzhledem <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> k tomu, že metody a používají <xref:System.Type> objekt k určení cílového typu, na který `value` je převeden, lze je použít k provedení dynamického převodu na objekt, jehož typ není v době kompilace znám. Všimněte si <xref:System.IConvertible> však, že provádění `value` musí stále podporovat tento převod.  
  
 Následující příklad ilustruje možnou implementaci <xref:System.IConvertible> rozhraní, `TemperatureCelsius` která umožňuje objekt převést na `TemperatureFahrenheit` objekt a naopak. Příklad definuje základní třídu `Temperature`, která <xref:System.IConvertible> implementuje rozhraní <xref:System.Object.ToString%2A?displayProperty=nameWithType> a přepíše metodu. Odvozené `TemperatureCelsius` a `TemperatureFahrenheit` třídy každý `ToType` přepsat `ToString` a metody základní třídy.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Následující příklad ilustruje několik volání <xref:System.IConvertible> těchto implementací převést `TemperatureCelsius` objekty na `TemperatureFahrenheit` objekty a naopak.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>Třída TypeConverter  
 Rozhraní .NET Framework také umožňuje definovat převaděč typu pro <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> vlastní typ rozšířením třídy a přidruženou <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> převaděč typu s typem prostřednictvím atributu. Následující tabulka zdůrazňuje rozdíly mezi tímto přístupem <xref:System.IConvertible> a implementací rozhraní pro vlastní typ.  
  
> [!NOTE]
> Podporu v době návrhu lze pro vlastní typ zajistit pouze tehdy, pokud byl definován konvertor typu.  
  
|Převod pomocí TypeConverter|Převod pomocí IConvertible|  
|------------------------------------|-----------------------------------|  
|Je implementována pro vlastní typ odvozením <xref:System.ComponentModel.TypeConverter>samostatné třídy z . Tato odvozená třída je přidružena k <xref:System.ComponentModel.TypeConverterAttribute> vlastnímu typu použitím atributu.|Je implementován vlastním typem za účelem převodu. Uživatel typu vyvolá metodu <xref:System.IConvertible> převodu na typu.|  
|Lze použít v době návrhu i v době spuštění.|Lze použít pouze v době spuštění.|  
|Používá odraz; proto je pomalejší než převod <xref:System.IConvertible>povolený .|Nepoužívá reflexi.|  
|Umožňuje obousměrný převod typu z vlastního typu na jiné datové typy a z jiných datových typů na vlastní typ. Například <xref:System.ComponentModel.TypeConverter> definované pro `MyType` umožňuje převody `MyType` z <xref:System.String> do `MyType` <xref:System.String>a z do .|Umožňuje převod z vlastního typu na jiné datové typy, nikoli však z jiných datových typů na vlastní typ.|  
  
 Další informace o použití převaděčů <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>typů k provádění převodů naleznete v tématu .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tabulky převodu typů](../../../docs/standard/base-types/conversion-tables.md)
