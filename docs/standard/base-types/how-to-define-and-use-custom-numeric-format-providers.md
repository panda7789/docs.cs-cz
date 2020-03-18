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
ms.openlocfilehash: 151bf40cf042517b7441b89688122373259dc7dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140061"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Postupy: Definování a používání vlastních poskytovatelů číselného formátu
Rozhraní .NET Framework poskytuje rozsáhlou kontrolu nad řetězcovou reprezentací číselných hodnot. Podporuje následující funkce pro přizpůsobení formátu číselných hodnot:  
  
- Standardní číselné formátovací řetězce, které poskytují předdefinovanou sadu formátů pro převod čísel na jejich řetězcovou reprezentaci. Můžete je použít s libovolnou metodou číselného formátování, například <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, která má `format` parametr. Podrobnosti naleznete v [tématu Standardní číselné formátovací řetězce](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
- Vlastní číselné formátovací řetězce, které poskytují sadu symbolů, které lze kombinovat k definování vlastních specifikátorů číselného formátu. Lze je také použít s libovolnou metodou <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>číselného formátování, například , která má `format` parametr. Podrobnosti naleznete [v tématu Vlastní číselné formátovací řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
- Vlastní <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> nebo objekty, které definují symboly a formátovací vzory použité při zobrazování řetězcových reprezentací číselných hodnot. Můžete je použít s libovolnou metodou číselného formátování, například <xref:System.Int32.ToString%2A>, která má `provider` parametr. Parametr se `provider` obvykle používá k určení formátování specifické pro jazykovou verzi.  
  
 V některých případech (například když aplikace musí zobrazit formátované číslo účtu, identifikační číslo nebo PSČ) jsou tyto tři techniky nevhodné. Rozhraní .NET Framework také umožňuje definovat formátovací objekt, <xref:System.Globalization.CultureInfo> který <xref:System.Globalization.NumberFormatInfo> není ani objekt, ani objekt k určení, jak je formátována číselná hodnota. Toto téma obsahuje podrobné pokyny pro implementaci takového objektu a poskytuje příklad, který formátuje telefonní čísla.  
  
### <a name="to-define-a-custom-format-provider"></a>Definování vlastního zprostředkovatele formátu  
  
1. Definujte třídu, <xref:System.IFormatProvider> která <xref:System.ICustomFormatter> implementuje rozhraní a.  
  
2. Implementujte <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodu. <xref:System.IFormatProvider.GetFormat%2A>je metoda zpětného volání, kterou metoda formátování <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> (například metoda) vyvolá k načtení objektu, který je skutečně zodpovědný za provedení vlastního formátování. Typická implementace <xref:System.IFormatProvider.GetFormat%2A> provádí následující:  
  
    1. Určuje, <xref:System.Type> zda objekt předaný jako <xref:System.ICustomFormatter> parametr metody představuje rozhraní.  
  
    2. Pokud parametr představuje <xref:System.ICustomFormatter> rozhraní, <xref:System.IFormatProvider.GetFormat%2A> vrátí objekt, který <xref:System.ICustomFormatter> implementuje rozhraní, které je zodpovědné za poskytování vlastní formátování. Vlastní objekt formátování se obvykle vrátí sám.  
  
    3. Pokud parametr nepředstavuje <xref:System.ICustomFormatter> rozhraní, <xref:System.IFormatProvider.GetFormat%2A> `null`vrátí .  
  
3. Implementujte <xref:System.ICustomFormatter.Format%2A> metodu. Tato metoda je <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volána metodou a je zodpovědná za vrácení řetězcové reprezentace čísla. Implementace metody obvykle zahrnuje následující:  
  
    1. Volitelně se ujistěte, že metoda je legitimně určena `provider` k poskytování služeb formátování kontrolou parametru. Pro formátování objektů, které <xref:System.IFormatProvider> <xref:System.ICustomFormatter>implementují oba `provider` a , to zahrnuje testování parametru rovnosti s aktuálním objektem formátování.  
  
    2. Určete, zda má objekt formátování podporovat vlastní specifikátory formátu. (Specifikátor formátu N může například znamenat, že telefonní číslo USA by mělo být vyprosit ve formátu NANP a "I" může indikovat výstup ve formátu ITU-T Recommendation E.123.) Pokud jsou použity specifikátory formátu, metoda by měla zpracovat konkrétní specifikátor formátu. Je předán metodě v `format` parametru. Pokud není k dispozici žádný specifikátor, hodnota parametru `format` je <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3. Načtěte číselnou hodnotu `arg` předanou metodě jako parametr. Proveďte jakékoli manipulace, které jsou požadovány k převodu na jeho řetězcové reprezentace.  
  
    4. Vrátí řetězcovou reprezentaci parametru. `arg`  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Použití vlastního objektu číselného formátování  
  
1. Vytvořte novou instanci vlastní třídy formátování.  
  
2. Zavolejte <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodu formátování, předejte jí vlastní objekt formátování, specifikátor <xref:System.String.Empty?displayProperty=nameWithType>formátování (nebo , pokud není použit) a číselnou hodnotu, která má být formátována.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje vlastního zprostředkovatele `TelephoneFormatter` číselného formátu s názvem, který převádí číslo, které představuje telefonní číslo USA do formátu NANP nebo E.123. Metoda zpracovává dva specifikátory formátu, "N" (který výstupy formátu NANP) a "I" (který výstupy mezinárodní formát E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Vlastní zprostředkovatel číselného formátu lze <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> použít pouze s metodou. Ostatní přetížení metody číselného formátování `ToString`(například ) které mají <xref:System.IFormatProvider> parametr <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> typu <xref:System.Type> všechny předat <xref:System.Globalization.NumberFormatInfo> implementaci objekt, který představuje typ. Na oplátku očekávají, že <xref:System.Globalization.NumberFormatInfo> metoda vrátí objekt. Pokud tomu tak není, je ignorována vlastní <xref:System.Globalization.NumberFormatInfo> zprostředkovatel číselného formátu a objekt pro aktuální jazykovou verzi se používá na jeho místě. V příkladu `TelephoneFormatter.GetFormat` metoda zpracovává možnost, že může být nevhodně předána metodě číselného formátování kontrolou `null` parametru metody a <xref:System.ICustomFormatter>vrácením, pokud představuje jiný typ než .  
  
 Pokud vlastní zprostředkovatel číselného formátu podporuje sadu specifikátorů formátu, ujistěte se, že poskytujete výchozí <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> chování, pokud není v položce formátu použité při volání metody zadán žádný specifikátor formátu. V příkladu je "N" výchozí specifikátor formátu. To umožňuje číslo převést na formátované telefonní číslo poskytnutím explicitního specifikátoru formátu. Následující příklad ilustruje takové volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ale také umožňuje převod uplatní, pokud není k dispozici žádný specifikátor formátu. Následující příklad ilustruje takové volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Pokud není definován žádný výchozí specifikátor <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> formátu, implementace metody by měla obsahovat například následující, aby rozhraní .NET mohla poskytovat formátování, které váš kód nepodporuje.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 V tomto příkladu metoda, která <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> implementuje má sloužit jako metoda <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> zpětného volání pro metodu. Proto zkoumá `formatProvider` parametr k určení, zda obsahuje odkaz `TelephoneFormatter` na aktuální objekt. Metoda však může být také volána přímo z kódu. V takovém případě můžete `formatProvider` parametr použít <xref:System.Globalization.CultureInfo> k <xref:System.Globalization.NumberFormatInfo> poskytnutí nebo objektu, který poskytuje informace o formátování specifické pro jazykovou verzi.  
  
## <a name="see-also"></a>Viz také

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
