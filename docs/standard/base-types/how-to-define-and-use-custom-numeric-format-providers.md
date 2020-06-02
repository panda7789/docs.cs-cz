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
ms.openlocfilehash: d12899fff7d9e6cb63728ba0b160b70fa2a41a1a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290510"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Postupy: Definování a používání vlastních poskytovatelů číselného formátu
.NET Framework poskytuje rozsáhlé řízení řetězcové reprezentace číselných hodnot. Podporuje následující funkce pro přizpůsobení formátu číselných hodnot:  
  
- Standardní řetězce číselného formátu, které poskytují předdefinované sady formátů pro převod čísel na jejich řetězcové vyjádření. Můžete je použít s libovolnou metodou číselného formátování, například <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> , která má `format` parametr. Podrobnosti naleznete v tématu [Standardní číselné formátovací řetězce](standard-numeric-format-strings.md).  
  
- Vlastní číselné formátovací řetězce, které poskytují sadu symbolů, které mohou být kombinovány pro definování vlastního specifikátoru číselného formátu. Lze je také použít s libovolnou metodou číselného formátování, například <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> , která má `format` parametr. Podrobnosti najdete v tématu [vlastní číselné formátovací řetězce](custom-numeric-format-strings.md).  
  
- Vlastní <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> objekty nebo, které definují symboly a vzory formátu používané v zobrazení řetězcových reprezentace číselných hodnot. Můžete je použít s libovolnou metodou číselného formátování, například <xref:System.Int32.ToString%2A> , která má `provider` parametr. Obvykle se `provider` parametr používá k určení formátování specifického pro jazykovou verzi.  
  
 V některých případech (například v případě, že aplikace musí zobrazit formátovaný číslo účtu, identifikační číslo nebo PSČ) tyto tři techniky nejsou vhodné. .NET Framework také umožňuje definovat objekt formátování, který není <xref:System.Globalization.CultureInfo> ani objekt, který <xref:System.Globalization.NumberFormatInfo> Určuje, jak má být číselná hodnota formátována. Toto téma poskytuje podrobné pokyny pro implementaci takového objektu a poskytuje příklad, který formátuje telefonní čísla.  
  
### <a name="to-define-a-custom-format-provider"></a>Definování vlastního poskytovatele formátu  
  
1. Definujte třídu, která implementuje <xref:System.IFormatProvider> rozhraní a <xref:System.ICustomFormatter> .  
  
2. Implementujte <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodu. <xref:System.IFormatProvider.GetFormat%2A>je metoda zpětného volání, kterou metoda formátování (například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Metoda) vyvolá k načtení objektu, který je skutečně zodpovědný za provádění vlastního formátování. Typická implementace aplikace <xref:System.IFormatProvider.GetFormat%2A> provede následující akce:  
  
    1. Určuje, zda <xref:System.Type> objekt předaný jako parametr metody představuje <xref:System.ICustomFormatter> rozhraní.  
  
    2. Pokud parametr představuje <xref:System.ICustomFormatter> rozhraní, <xref:System.IFormatProvider.GetFormat%2A> vrátí objekt, který implementuje <xref:System.ICustomFormatter> rozhraní zodpovědné za poskytnutí vlastního formátování. Obvykle se vlastní objekt formátování vrátí sám.  
  
    3. Pokud parametr nepředstavuje <xref:System.ICustomFormatter> rozhraní, <xref:System.IFormatProvider.GetFormat%2A> vrátí `null` .  
  
3. Implementujte <xref:System.ICustomFormatter.Format%2A> metodu. Tato metoda je volána <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodou a zodpovídá za vrácení řetězcové reprezentace čísla. Implementace metody obvykle zahrnuje následující:  
  
    1. Volitelně se ujistěte, že je metoda oprávněná k poskytování služeb formátování prozkoumáním `provider` parametru. Pro formátování objektů, které implementují i <xref:System.IFormatProvider> <xref:System.ICustomFormatter> , to zahrnuje testování `provider` parametru pro rovnost s aktuálním objektem formátování.  
  
    2. Určete, zda má objekt formátování podporovat vlastní specifikátory formátu. (Například specifikátor formátu "N" může znamenat, že telefonní číslo v USA by mělo mít výstup ve formátu NANP a "I" může označovat výstup ve formátu doporučení ITU-T E. 123.) Pokud jsou použity specifikátory formátu, metoda by měla zpracovat konkrétní specifikátor formátu. Je předána metodě v `format` parametru. Pokud není k dispozici žádný specifikátor, hodnota `format` parametru je <xref:System.String.Empty?displayProperty=nameWithType> .  
  
    3. Načte číselnou hodnotu předanou metodě jako `arg` parametr. Pro převod na jeho řetězcovou reprezentaci je nutné provést jakékoli manipulace.  
  
    4. Vrátí řetězcovou reprezentaci `arg` parametru.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Použití vlastního objektu formátování čísel  
  
1. Vytvoří novou instanci třídy vlastního formátování.  
  
2. Zavolejte <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodu formátování a předejte jí vlastní objekt formátování, specifikátor formátování (nebo <xref:System.String.Empty?displayProperty=nameWithType> , pokud se nepoužívá) a číselnou hodnotu, která má být formátována.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje vlastní poskytovatele číselného formátu s názvem `TelephoneFormatter` , který převede číslo představující telefonní číslo v USA na jeho NANP nebo formát E. 123. Metoda zpracovává dva specifikátory formátu, "N" (které výstupují formát NANP) a "I" (výstup mezinárodního formátu E. 123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Vlastního poskytovatele číselného formátu lze použít pouze s <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodou. Další přetížení metod číselného formátování (například `ToString` ), které mají parametr typu <xref:System.IFormatProvider> All Pass <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementující <xref:System.Type> objekt, který představuje <xref:System.Globalization.NumberFormatInfo> typ. V případě, že jsou vráceny, očekávají metodu, která vrátí <xref:System.Globalization.NumberFormatInfo> objekt. V takovém případě se poskytovatel vlastního číselného formátu ignoruje a místo toho se <xref:System.Globalization.NumberFormatInfo> použije objekt pro aktuální jazykovou verzi. V tomto příkladu `TelephoneFormatter.GetFormat` metoda zpracovává možnost, že může být nevhodně předána metodě číselného formátování, a to zkoumáním parametru metody a vrácením `null` , pokud představuje jiný typ než <xref:System.ICustomFormatter> .  
  
 Pokud vlastní zprostředkovatel číselného formátu podporuje sadu specifikátorů formátu, ujistěte se, že zadáváte výchozí chování, pokud není zadán žádný specifikátor formátu v položce formátu používané při <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volání metody. V příkladu je výchozím specifikátorem formátu "N". To umožňuje, aby číslo bylo převedeno na formátované telefonní číslo poskytnutím explicitního specifikátoru formátu. Následující příklad znázorňuje takové volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Ale také umožňuje, aby k převodu docházelo, pokud není k dispozici žádný specifikátor formátu. Následující příklad znázorňuje takové volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Pokud není definován žádný výchozí specifikátor formátu, vaše implementace <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metody by měla obsahovat kód jako následující, aby rozhraní .NET mohlo poskytovat formátování, které váš kód nepodporuje.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 V případě tohoto příkladu má metoda, která implementuje, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> záměr sloužit jako metoda zpětného volání pro <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodu. Proto ověří `formatProvider` parametr a určí, zda obsahuje odkaz na aktuální `TelephoneFormatter` objekt. Metodu lze však také volat přímo z kódu. V takovém případě můžete použít `formatProvider` parametr k poskytnutí <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> objektu nebo, který poskytuje informace o formátování specifické pro jazykovou verzi.
