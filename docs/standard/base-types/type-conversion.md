---
title: "Převod typů v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d8bbf57625e1d944ab4e97235e718eef7b61a3a4
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="type-conversion-in-the-net-framework"></a>Převod typů v rozhraní .NET Framework
<a name="top"></a> Každá hodnota má přidružený typ, který definuje atributy, jako je množství přidělené místo na hodnotu rozsahu možných hodnot, které může mít, a členy které to umožní. Mnoho hodnot lze vyjádřit ve formě více než jednoho typu. Například hodnotu 4 lze vyjádřit jako celé číslo nebo jako hodnotu s plovoucí desetinnou čárkou. Převod typu vytvoří hodnotu v novém typu, která je ekvivalentní hodnotě starého typu, ale nutně nezachová identitu (nebo přesnou hodnotu) původního objektu.  
  
 Rozhraní .NET Framework automaticky podporuje následující převody:  
  
-   Převod z odvozené třídy základní třídy. To znamená, například, že instance všechny třídu nebo strukturu můžete převést na <xref:System.Object> instance.  Tento převod nevyžaduje operátor přetypování nebo převod.  
  
-   Převod ze základní třídy zpět na původní odvozené třídy. V jazyce C# vyžaduje tento převod operátor přetypování. V jazyce Visual Basic, vyžaduje `CType` operátor Pokud `Option Strict` zapnutý.  
  
-   Převod z typu, který implementuje rozhraní rozhraní objektu, která představuje tohoto rozhraní. Tento převod nevyžaduje operátor přetypování nebo převod.  
  
-   Převod z objektu rozhraní zpět na původní typ, který implementuje rozhraní.  V jazyce C# vyžaduje tento převod operátor přetypování. V jazyce Visual Basic, vyžaduje `CType` operátor Pokud `Option Strict` zapnutý.  
  
 Kromě těchto Automatické převody [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] poskytuje několik funkcí, které podporují převod vlastní typu. Patří mezi ně například:  
  
-   `Implicit` Operátor, který definuje dostupné rozšiřující převody mezi typy. Další informace najdete v tématu [implicitní převod s implicitním operátorem](#implicit_conversion_with_the_implicit_operator) části.  
  
-   `Explicit` Operátor, který definuje dostupné zužující převody mezi typy. Další informace najdete v tématu [explicitní převod s explicitní operátor](#explicit_conversion_with_the_explicit_operator) části.  
  
-   <xref:System.IConvertible> Rozhraní, které definuje převody každý základní datový typ rozhraní .NET Framework. Další informace najdete v tématu [rozhraní IConvertible](#the_iconvertible_interface) části.  
  
-   <xref:System.Convert> Třídy, která poskytuje sadu metod, které implementují metody v <xref:System.IConvertible> rozhraní. Další informace najdete v tématu [Třída Convert](#Convert) části.  
  
-   <xref:System.ComponentModel.TypeConverter> Třída, která je základní třídu, která můžete rozšířit pro zajištění podpory převodu zadaného typu k žádným jiným typem. Další informace najdete v tématu [Třída TypeConverter](#the_typeconverter_class) části.  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Implicitní převod s implicitním operátorem  
 Rozšiřující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, který má buď více omezený rozsah, nebo více omezený seznam členů než cílový typ. Rozšiřující převody nemohou způsobit ztrátu dat (ačkoliv mohou způsobit ztrátu přesnosti). Vzhledem k tomu, že nemůže dojít ke ztrátě dat, mohou kompilátory zpracovat převod implicitně nebo transparentně, aniž by bylo nutné použít metodu explicitního převodu nebo operátor přetypování.  
  
> [!NOTE]
>  Ačkoli kód, který provede implicitní převod, může volat metodu převodu nebo použít operátor přetypování, není jejich používání vyžadováno kompilátory, které podporují implicitní převody.  
  
 Například <xref:System.Decimal> podporuje implicitní převod z typu <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>, a <xref:System.UInt64> hodnoty. Následující příklad ukazuje některé z těchto implicitní převody v přiřazování hodnot k <xref:System.Decimal> proměnné.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Pokud kompilátor určitého jazyka podporuje vlastní operátory, můžete ve vlastních typech definovat také implicitní převody. Následující příklad uvádí částečnou implementaci podepsaný byte – datový typ s názvem `ByteWithSign` používající reprezentace přihlášení a rozsahem. Podporuje implicitní převod z <xref:System.Byte> a <xref:System.SByte> hodnoty k `ByteWithSign` hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Potom můžete deklarovat kód klienta `ByteWithSign` proměnné a přiřaďte ho <xref:System.Byte> a <xref:System.SByte> hodnoty bez provedení žádné explicitní převody nebo pomocí jakýchkoli operátorů přetypování, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Zpět na začátek](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Explicitní převod s explicitním operátorem  
 Zužující převody zahrnují vytvoření nové hodnoty z hodnoty existujícího typu, která má buď větší rozsah, nebo větší seznam členů než cílový typ. Vzhledem k tomu, že zužující převod může mít za následek ztrátu dat, kompilátory často vyžadují, aby byl převod vytvořen explicitně prostřednictvím volání metody převodu nebo operátoru přetypování. To znamená, že převod musí být zpracován explicitně v kódu vývojáře.  
  
> [!NOTE]
>  Hlavní účel museli metoda převodu nebo operátor přetypování pro zužující převody je to, aby vývojáři vědět dojít ke ztrátě dat nebo <xref:System.OverflowException> , aby mohlo být zpracováno v kódu. Některé kompilátory však mohou tento požadavek zmírnit. Například v Visual Basic, pokud `Option Strict` je vypnuto (výchozí nastavení), Visual Basic – kompilátor pokusu o provedení zužující převody implicitně.  
  
 Například <xref:System.UInt32>, <xref:System.Int64>, a <xref:System.UInt64> typy dat mají rozsahy, které překročí <xref:System.Int32> datového typu, jak ukazuje následující tabulka.  
  
|Typ|Porovnání s rozsahem Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a <xref:System.Int64.MinValue?displayProperty=nameWithType> je menší než (má negativní větší rozsah než) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType> je větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Zpracovat takové zužující převody [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] umožňuje typům definovat `Explicit` operátor. Kompilátory jednotlivých jazyků poté můžete implementovat tento operátor pomocí vlastní syntaxe nebo člen <xref:System.Convert> třídy lze volat pro převod provést. (Další informace o <xref:System.Convert> třídy najdete v tématu [Třída Convert](#Convert) dál v tomto tématu.) Následující příklad ukazuje použití funkcí jazyka ke zpracování explicitního převodu těchto potenciálně out-of-range celočíselné hodnoty k <xref:System.Int32> hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Explicitní převody může mít různé výsledky v různých jazycích a tyto výsledky se může lišit od hodnoty vrácené odpovídající <xref:System.Convert> metoda. Například pokud <xref:System.Double> hodnota 12.63251 jsou převedeny na <xref:System.Int32>, jazyka Visual Basic `CInt` metoda a rozhraní .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> metoda zaokrouhlí <xref:System.Double> vrátit hodnotu 13, ale jazyka C# `(int)` – operátor zkrátí <xref:System.Double> vrátit hodnotu 12. Podobně platí, jazyka C# `(int)` operátor nepodporuje převod logickou hodnotu na celé číslo, ale Visual Basicu `CInt` metoda převede hodnotu `true` na hodnotu -1. Na druhé straně <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> metoda převede hodnotu `true` na 1.  
  
 Většina kompilátorů umožňuje, aby explicitní převody byly prováděny zkontrolovaným, nebo nezkontrolovaným způsobem. Při převodu z zaškrtnuté, <xref:System.OverflowException> se vyvolá, když hodnota typu k převedení je mimo rozsah typu cíle. Pokud je nezkontrolovaný převod proveden za stejných podmínek, nemusí převod vyvolat výjimku, ale stejné chování bude nedefinováno a může mít za následek nesprávnou hodnotu.  
  
> [!NOTE]
>  V jazyce C#, zaškrtnutí převody lze provést pomocí `checked` – klíčové slovo společně s operátor přetypování nebo zadáním `/checked+` – možnost kompilátoru. Naopak, nezkontrolované převody lze provést pomocí `unchecked` – klíčové slovo společně s operátor přetypování nebo zadáním `/checked-` – možnost kompilátoru. Ve výchozím nastavení jsou explicitní převody nezkontrolované. V jazyce Visual Basic zaškrtnutí převody lze provést tak, že smažete **odebrat kontroly přetečení celých** políčko v projektu **Upřesnit nastavení kompilátoru** dialogové okno, nebo zadáním `/removeintchecks-`– možnost kompilátoru. Naopak nezaškrtnuté převody lze provést výběrem **odebrat kontroly přetečení celých** políčko v projektu **Upřesnit nastavení kompilátoru** dialogové okno nebo zadáním `/removeintchecks+`– možnost kompilátoru. Ve výchozím nastavení jsou explicitní převody zkontrolované.  
  
 V následujícím příkladu C# `checked` a `unchecked` klíčová slova pro ilustraci rozdíl v chování, když je hodnota mimo rozsah <xref:System.Byte> jsou převedeny na <xref:System.Byte>. Checked převod vyvolá výjimku, ale není zaškrtnuto převod přiřadí <xref:System.Byte.MaxValue?displayProperty=nameWithType> k <xref:System.Byte> proměnné.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Pokud konkrétní jazykový kompilátor podporuje vlastní přetížené operátory, můžete ve vlastních typech definovat také explicitní převody. Následující příklad uvádí částečnou implementaci podepsaný byte – datový typ s názvem `ByteWithSign` používající reprezentace přihlášení a rozsahem. Podporuje explicitní převod <xref:System.Int32> a <xref:System.UInt32> hodnoty k `ByteWithSign` hodnoty.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Potom můžete deklarovat kód klienta `ByteWithSign` proměnné a přiřaďte ho <xref:System.Int32> a <xref:System.UInt32> hodnoty Pokud přiřazení zahrnují operátor přetypování nebo metodu převodu, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>Rozhraní IConvertible  
 Pro podporu převod libovolného typu common language runtime základní typ, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] poskytuje <xref:System.IConvertible> rozhraní. Implementující typ je vyžadován pro následující akce:  
  
-   Metoda, která vrátí <xref:System.TypeCode> implementujícího typu.  
  
-   Metody k převedení implementujícího typu do každého common language runtime základního typu (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>a tak dále).  
  
-   Zobecněná metoda převodu k převedení instance implementujícího typu na jiný určený typ. Převody, které nejsou podporovány by měla vyvolat <xref:System.InvalidCastException>.  
  
 Každý běžné typ základní runtime jazyka (který je <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>, a <xref:System.UInt64>), a taky <xref:System.DBNull> a <xref:System.Enum> typy, implementovat <xref:System.IConvertible> rozhraní. Ty jsou ale implementace explicitního rozhraní. Převod metodu lze volat pouze prostřednictvím <xref:System.IConvertible> proměnné rozhraní, jak ukazuje následující příklad. Tento příklad převede <xref:System.Int32> hodnotu na odpovídající <xref:System.Char> hodnotu.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Pokud je požadavek volání metody převodu uplatněn na rozhraní a nikoli na implementující typ, jsou implementace explicitního rozhraní poměrně nákladné. Místo toho doporučujeme volat odpovídajícího člena <xref:System.Convert> třídy pro převod mezi common language runtime základní typy. Další informace najdete v části Další [Třída Convert](#Convert).  
  
> [!NOTE]
>  Kromě <xref:System.IConvertible> rozhraní a <xref:System.Convert> třída poskytované [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], mohou jednotlivé jazyky také poskytnout způsoby, jak provést převody. Například C# používá operátory přetypování. Visual Basic, jako používá funkce převodu implementované kompilátoru `CType`, `CInt`, a `DirectCast`.  
  
 Ve většině případů <xref:System.IConvertible> rozhraní je navržen pro podporu převod mezi základními typy v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Rozhraní lze však implementovat také pomocí vlastního typu, a podpořit tak převod tohoto typu na vlastní typy. Další informace najdete v části [vlastní převod s metodou ChangeType](#ChangeType) dál v tomto tématu.  
  
 [Zpět na začátek](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Třída Convert  
 I když každý základní typ <xref:System.IConvertible> implementace rozhraní lze volat pro provedení převedení typu, volání metod <xref:System.Convert?displayProperty=nameWithType> třída je doporučeným způsobem jazykově neutrální převést z jednoho základního typu. Kromě toho <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metoda lze převést na zadaný typ vlastní k jinému typu.  
  
### <a name="conversions-between-base-types"></a>Převody mezi základními typy  
 <xref:System.Convert> Třída poskytuje jazykově neutrální způsob, jak provést převody mezi základní typy a je k dispozici pro všechny jazyky, které cílí modul common language runtime. Poskytuje kompletní sadu metody pro oba rozšíření a zúžení převodů a vyvolá <xref:System.InvalidCastException> pro převody, které nejsou podporovány (například převod <xref:System.DateTime> hodnotu na celočíselnou hodnotu). Zužující převody jsou prováděny v zaškrtnuté kontextu a <xref:System.OverflowException> je vyvolána, pokud převod selže.  
  
> [!IMPORTANT]
>  Protože <xref:System.Convert> třída obsahuje metody pro převod na a z každého základního typu, eliminuje nutnost volání každý základní typ <xref:System.IConvertible> implementace explicitního rozhraní.  
  
 Následující příklad ukazuje použití <xref:System.Convert?displayProperty=nameWithType> třída provést několik rozšíření a zúžení převodů mezi základní typy rozhraní .NET Framework.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 V některých případech, zejména při převodu do a z hodnot s plovoucí desetinnou čárkou, převod může zahrnovat ztrátu přesnosti, i když nevyvolá <xref:System.OverflowException>. Následující příklad znázorňuje tuto ztrátu přesnosti. V prvním případě <xref:System.Decimal> má hodnotu menší přesnost (méně významných číslic) Pokud je převést na <xref:System.Double>. V druhém případě <xref:System.Double> je hodnota zaokrouhlena z 42.72 43 pro dokončení převodu.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Pro tabulku, která uvádí, jak rozšíření a zúžení převodů podporovaných <xref:System.Convert> třídy najdete v tématu [tabulky převodu typů](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>Vlastní převody pomocí metody ChangeType  
 Kromě podpory převodů na jakýkoli základní typy <xref:System.Convert> třídu lze použít pro vlastní typ převést na jeden nebo více předdefinovaných typů. Provádí tento převod <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu, která zabalí volání <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> metodu `value` parametr. To znamená, že objekt reprezentovaný rozhraním `value` parametr musí poskytnout implementaci <xref:System.IConvertible> rozhraní.  
  
> [!NOTE]
>  Protože <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> a <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody použití <xref:System.Type> objekt, který chcete zadat typ cíle, ke kterému `value` je převést, použitím proveďte dynamické převod na objekt, jehož typ není známý v době kompilace. Všimněte si však, že <xref:System.IConvertible> implementace `value` musí podporovat i nadále tento převod.  
  
 Následující příklad ilustruje možnou implementaci <xref:System.IConvertible> rozhraní, které umožňuje `TemperatureCelsius` objekt má být převeden na `TemperatureFahrenheit` objektu a naopak. V příkladu definuje základní třídu, `Temperature`, která implementuje <xref:System.IConvertible> rozhraní a přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda. Odvozené `TemperatureCelsius` a `TemperatureFahrenheit` třídy každý přepsání `ToType` a `ToString` metody základní třídy.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Následující příklad ukazuje několik volání tyto <xref:System.IConvertible> implementace převést `TemperatureCelsius` objekty ke `TemperatureFahrenheit` objekty a naopak.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>Třída TypeConverter  
 Rozhraní .NET Framework také umožňuje definovat převaděč typů pro vlastní typ tím, že rozšíří <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> třídy a přidružení převaděč typů s typem prostřednictvím <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> atribut. Následující tabulka obsahuje rozdíly mezi tento přístup a implementace <xref:System.IConvertible> rozhraní pro vlastní typ.  
  
> [!NOTE]
>  Podporu v době návrhu lze pro vlastní typ zajistit pouze tehdy, pokud byl definován konvertor typu.  
  
|Převod pomocí TypeConverter|Převod pomocí IConvertible|  
|------------------------------------|-----------------------------------|  
|Je implementována pro vlastní typ odvozením samostatné třídy z <xref:System.ComponentModel.TypeConverter>. Tato odvozená třída souvisí s vlastním typem použitím <xref:System.ComponentModel.TypeConverterAttribute> atribut.|Je implementován vlastním typem za účelem převodu. Uživatel typu vyvolá <xref:System.IConvertible> metoda převodu typu.|  
|Lze použít v době návrhu i v době spuštění.|Lze použít pouze v době spuštění.|  
|Používá reflexe. Proto je pomalejší než převod povolený <xref:System.IConvertible>.|Nepoužívá reflexi.|  
|Umožňuje obousměrný převod typu z vlastního typu na jiné datové typy a z jiných datových typů na vlastní typ. Například <xref:System.ComponentModel.TypeConverter> definované pro `MyType` umožňuje převody z `MyType` k <xref:System.String>a z <xref:System.String> k `MyType`.|Umožňuje převod z vlastního typu na jiné datové typy, nikoli však z jiných datových typů na vlastní typ.|  
  
 Další informace o použití převaděče typu k provedení převody najdete v tématu <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Convert?displayProperty=nameWithType>  
 <xref:System.IConvertible>  
 [Tabulky převodu typů](../../../docs/standard/base-types/conversion-tables.md)
