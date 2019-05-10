---
title: 'Postupy: Definování a používání vlastních poskytovatelů číselného formátu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37c9140db390c55c9cab4e8a3203287d2dd12725
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64634242"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Postupy: Definování a používání vlastních poskytovatelů číselného formátu
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje rozsáhlou kontrolu nad řetězcové reprezentace číselných hodnot. Přizpůsobení formátu číselných hodnot podporuje následující funkce:  
  
- Řetězce standardního číselného formátu, což poskytuje sadu předdefinovaných formátů pro převod čísla na jeho řetězcovou reprezentaci. Můžete využít s jakoukoli metodou číselného formátování, jako například <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, který má `format` parametru. Podrobnosti najdete v tématu [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
- Vlastní číselné formátovací řetězce, které poskytují sadu symboly, které mohou být kombinovány definovat vlastní specifikátory číselného formátu. Můžete je také použít s libovolnou metodou číselného formátování, jako například <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, který má `format` parametru. Podrobnosti najdete v tématu [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
- Vlastní <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.NumberFormatInfo> objekty, které definují symboly a formátování vzorů používaných pro zobrazení řetězcové reprezentace číselných hodnot. Můžete využít s jakoukoli metodou číselného formátování, jako například <xref:System.Int32.ToString%2A>, který má `provider` parametru. Obvykle `provider` parametr se používá k určení formátování specifické pro jazykovou verzi.  
  
 V některých případech (například když musí aplikace zobrazit formátované číslo účtu, identifikační číslo nebo poštovní směrovací číslo) jsou tyto tři techniky nevhodný. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také umožňuje definovat formátovací objekt, který není ani <xref:System.Globalization.CultureInfo> ani <xref:System.Globalization.NumberFormatInfo> zjistíte, jak číselnou hodnotu ve formátu. Toto téma obsahuje podrobné pokyny pro implementaci takového objektu a poskytuje příklad, který formátuje telefonních čísel.  
  
### <a name="to-define-a-custom-format-provider"></a>K definování vlastního poskytovatele formátu  
  
1. Definujte třídu, která implementuje <xref:System.IFormatProvider> a <xref:System.ICustomFormatter> rozhraní.  
  
2. Implementace <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. <xref:System.IFormatProvider.GetFormat%2A> je metoda zpětného volání, který použije metoda formátování (například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda) vyvolá při načtení objektu, který je ve skutečnosti odpovědný za provedení vlastní formátování. Obvyklá implementace metody <xref:System.IFormatProvider.GetFormat%2A> provede následující akce:  
  
    1. Určuje, zda <xref:System.Type> objekt předán jako metoda představuje parametr <xref:System.ICustomFormatter> rozhraní.  
  
    2. Pokud parametr představuje <xref:System.ICustomFormatter> rozhraní, <xref:System.IFormatProvider.GetFormat%2A> vrátí objekt, který implementuje <xref:System.ICustomFormatter> rozhraní, které je odpovědný za poskytnutí vlastní formátování. Vlastní objekt obvykle vrací samu sebe.  
  
    3. Pokud parametr nepředstavuje <xref:System.ICustomFormatter> rozhraní, <xref:System.IFormatProvider.GetFormat%2A> vrátí `null`.  
  
3. Implementace <xref:System.ICustomFormatter.Format%2A> metody. Tato metoda je volána metodou <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody a je zodpovědný za vrácení řetězcové vyjádření čísla. Implementace metody obvykle zahrnuje následující:  
  
    1. Volitelně, ujistěte se, že metoda je rozmyslet určená k zajištění služeb formátování prozkoumáním `provider` parametru. Pro formátování objektů, které implementují <xref:System.IFormatProvider> a <xref:System.ICustomFormatter>, to zahrnuje testování `provider` parametr rovnosti s aktuálním objektem formátování.  
  
    2. Určení, zda objekt formátování by měla podporovat specifikátoru vlastního formátu. (Například specifikátor formátu "N" může znamenat, že telefonní číslo USA by měl být výstup ve formátu NANP, a "I" může znamenat výstup ve formátu ITU-T E.123 doporučení.) Pokud specifikátory formátu se používají, měla by metoda zpracovat specifikátor formátu. V metodě je předána `format` parametru. Pokud žádný specifikátor není k dispozici, hodnota `format` parametr <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3. Vrátit číselnou hodnotu předaný metodě jako `arg` parametru. Provedení libovolné manipulace se vyžadují pro převod na jeho řetězcovou reprezentaci.  
  
    4. Vrátí řetězcovou reprezentaci `arg` parametru.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Chcete-li použít vlastní číselné formátovací objekt  
  
1. Vytvořte novou instanci třídy vlastní formátování.  
  
2. Volání <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> formátování, předáním vlastního formátování objektu, specifikátor formátování (nebo <xref:System.String.Empty?displayProperty=nameWithType>, pokud se používá) a číselnou hodnotu, která má být formátováno.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje vlastní číselné formátovací poskytovatele s názvem `TelephoneFormatter` , která převede číslo, které představuje telefonní číslo USA do jeho NANP nebo E.123 formátu. Tato metoda obsluhuje dva specifikátory formátu "N" (který výstupy ve formátu NANP) a "I" (jejímž výstupem v mezinárodním formátu E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Poskytovatel vlastního číselného formátu lze použít pouze s <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody. Dalších přetížení metody formátování čísel (jako `ToString`), které mají parametr typu <xref:System.IFormatProvider> se všemi pass <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace <xref:System.Type> objekt, který reprezentuje <xref:System.Globalization.NumberFormatInfo> typu. Na oplátku očekávají metodu pro návrat <xref:System.Globalization.NumberFormatInfo> objektu. Pokud tomu tak není, je ignorován zprostředkovatele vlastního číselného formátu a <xref:System.Globalization.NumberFormatInfo> objektů pro aktuální jazykovou verzi je použít na příslušné místo. V tomto příkladu `TelephoneFormatter.GetFormat` obsluhovala možnost, která může být nesprávně předána číselného formátování metoda kontrolou parametr metody a vrací `null` , pokud představuje typu jiného než <xref:System.ICustomFormatter>.  
  
 Pokud zprostředkovatele vlastního číselného formátu podporuje sadu specifikátorů formátu, ujistěte se, že zadáte výchozí chování, pokud není zadán žádný specifikátor formátu v položce formátu, který je používán <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volání metody. V tomto příkladu je "N" výchozí specifikátor formátu. To umožňuje číslo má být převeden na formátované telefonní číslo, tím, že poskytuje explicitního specifikátoru formátu. Následující příklad ukazuje volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ale umožňuje také dojít, pokud je k dispozici žádný format specifikátor převodu. Následující příklad ukazuje volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Pokud není definován žádný specifikátor formátu výchozí, implementace <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda by měla obsahovat například následující kód, tak že .NET může poskytnout formátování, že váš kód nepodporuje.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 V tomto příkladu metoda, která implementuje <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> má sloužit jako metody zpětného volání pro <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody. Proto zkontroluje `formatProvider` parametr k určení, zda obsahuje odkaz na aktuální `TelephoneFormatter` objektu. Přímo z kódu však lze také volat metodu. V takovém případě můžete použít `formatProvider` parametr k poskytování <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Je možné zkompilovat kód v příkazovém řádku pomocí souboru csc.exe nebo vb.exe. Chcete-li zkompilovat kód v sadě Visual Studio, vložte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
