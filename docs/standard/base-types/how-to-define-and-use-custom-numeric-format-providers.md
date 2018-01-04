---
title: "Postupy: Definování a používání vlastních poskytovatelů číselného formátu"
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
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f8f06335d96b3e71f14b3df6b40ef3691c0915f1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Postupy: Definování a používání vlastních poskytovatelů číselného formátu
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje rozsáhlou kontrolu nad řetězcová reprezentace číselné hodnoty. Podporuje následující funkce pro přizpůsobení formát číselné hodnoty:  
  
-   Standardní řetězce formátu čísla, které poskytují předdefinovanou sadu formátů pro převod na jejich řetězcovou reprezentaci čísla. Můžete je použít s libovolnou metodou číselného formátování, jako například <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, který má `format` parametr. Podrobnosti najdete v tématu [standardní číselných řetězců formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
-   Vlastní řetězce číselného formátu, které poskytují sadu symbolů, které mohou být kombinovány definovat vlastní specifikátory číselného formátu. Můžete je také použít s libovolnou metodou číselného formátování, jako například <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, který má `format` parametr. Podrobnosti najdete v tématu [vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   Vlastní <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.NumberFormatInfo> objekty, které definují symboly a vzorky formátu použité při zobrazování řetězec reprezentace číselné hodnoty. Můžete je použít s libovolnou metodou číselného formátování, jako například <xref:System.Int32.ToString%2A>, který má `provider` parametr. Obvykle `provider` parametr se používá k určení formátování specifické pro jazykovou verzi.  
  
 V některých případech (například když aplikace musí zobrazit formátované číslo účtu, identifikační číslo nebo poštovní směrovací číslo) jsou tyto tři techniky nevhodných. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také umožňuje definovat formátovací objekt, který je ani <xref:System.Globalization.CultureInfo> ani <xref:System.Globalization.NumberFormatInfo> objektem pro určení formátování číselná hodnota. Toto téma obsahuje podrobné pokyny pro implementaci takového objektu a poskytuje příklad, který zformátuje telefonních čísel.  
  
### <a name="to-define-a-custom-format-provider"></a>Chcete-li definovat vlastní formát zprostředkovatele  
  
1.  Definice třídy, která implementuje <xref:System.IFormatProvider> a <xref:System.ICustomFormatter> rozhraní.  
  
2.  Implementace <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metoda. <xref:System.IFormatProvider.GetFormat%2A>je metoda zpětného volání, metoda formátování (například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda) vyvolá pro načtení objektu, který je ve skutečnosti odpovědný za provádění vlastní formátování. Typická implementace <xref:System.IFormatProvider.GetFormat%2A> provede následující akce:  
  
    1.  Určuje, zda <xref:System.Type> objekt předaný jako metodu představuje parametr <xref:System.ICustomFormatter> rozhraní.  
  
    2.  Pokud parametr představuje <xref:System.ICustomFormatter> rozhraní <xref:System.IFormatProvider.GetFormat%2A> vrátí objekt, který implementuje <xref:System.ICustomFormatter> rozhraní, která zodpovídá za poskytování vlastní formátování. Vlastní objekt obvykle vrátí samu sebe.  
  
    3.  Pokud parametr nepředstavuje <xref:System.ICustomFormatter> rozhraní <xref:System.IFormatProvider.GetFormat%2A> vrátí `null`.  
  
3.  Implementace <xref:System.ICustomFormatter.Format%2A> metoda. Tato metoda je volána <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda a je odpovědná za vrací řetězcovou reprezentaci číslo. Implementace metody obvykle zahrnuje následující:  
  
    1.  Volitelně se ujistěte, že metoda oprávněna k poskytování služeb formátování ověřením `provider` parametr. Pro objekty, které implementují obě formátu <xref:System.IFormatProvider> a <xref:System.ICustomFormatter>, to zahrnuje testování `provider` parametr rovnosti s aktuálním objektem formátování.  
  
    2.  Určí, zda objekt formátování by měly podporovat vlastní specifikátory formátu. (Například specifikátor formátu "N" může znamenat, že US telefonní číslo musí být výstup ve formátu NANP, a "I" může znamenat výstup ve formátu ITU-T E.123 doporučení.) Pokud se používají specifikátory formátu, metoda by měla řídit specifikátor formátu. Je předaný metodě v `format` parametr. Pokud žádné specifikátor je k dispozici, hodnota `format` parametr <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3.  Vrátit číselnou hodnotu předaný metodě jako `arg` parametr. Proveďte, ať manipulace je potřeba ho převést na jeho řetězcová reprezentace.  
  
    4.  Vrátí řetězcovou reprezentaci `arg` parametr.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Chcete-li použít vlastní objekt číselného formátování  
  
1.  Vytvořte novou instanci třídy vlastní formátování.  
  
2.  Volání <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> formátování metoda, předání vlastní objekt, formátování specifikátor (nebo <xref:System.String.Empty?displayProperty=nameWithType>, pokud se nepoužívá jeden) a číselnou hodnotu, která má být formátována.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje vlastní číselného formátu zprostředkovatele s názvem `TelephoneFormatter` , která převádí číslo, které představuje USA telefonní číslo jeho NANP nebo E.123 formátu. Tato metoda obsluhuje dva specifikátory formátu "N" (což výstupy ve formátu NANP) a "I" (což výstupy v mezinárodním formátu E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Poskytovatel vlastního číselného formátu lze použít pouze s <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda. Další přetížení metody formátování čísel (například `ToString`) které mají parametr typu <xref:System.IFormatProvider> všechny předat <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace <xref:System.Type> objekt, který reprezentuje <xref:System.Globalization.NumberFormatInfo> typu. V očekáváno, že metoda vrátí <xref:System.Globalization.NumberFormatInfo> objektu. Pokud ne, je ignorován poskytovatel vlastního číselného formátu a <xref:System.Globalization.NumberFormatInfo> objektu pro aktuální jazykovou verzi je použít na příslušné místo. V příkladu `TelephoneFormatter.GetFormat` metoda zpracovává případ, že může být nevhodně předán číselného metoda kontrolou parametru metody a vrácení `null` , pokud jiné než představuje typ <xref:System.ICustomFormatter>.  
  
 Pokud poskytovatel vlastního číselného formátu podporuje sadu specifikátory formátu, ujistěte se, že zadáte výchozí chování, pokud není zadán žádný specifikátor formátu v položce formátu použité v <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volání metody. V příkladu "N" je výchozí specifikátor formátu. To umožňuje číslo má být převeden na formátované telefonní číslo, tím, že poskytuje specifikátor explicitní formátu. Následující příklad ukazuje volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Můžete ale také umožňuje převod na dojít, pokud je k dispozici žádné specifikátor formátu. Následující příklad ukazuje volání metody.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Pokud není definován žádný výchozí formát specifikátor, vaši implementaci <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda by měla obsahovat kód, například následující, že .NET můžou poskytovat formátování které kódu není podporováno.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 V případě tohoto příkladu metoda, která implementuje <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> má sloužit jako metody zpětného volání pro <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda. Proto zkontroluje `formatProvider` parametr k určení, zda obsahuje odkaz na aktuální `TelephoneFormatter` objektu. Ale metody lze také volat přímo z kódu. V takovém případě můžete použít `formatProvider` parametr k poskytování <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Je možné zkompilovat kód v příkazovém řádku pomocí souboru csc.exe nebo vb.exe. Chcete-li kód zkompilovat v rámci [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vložte jej do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
