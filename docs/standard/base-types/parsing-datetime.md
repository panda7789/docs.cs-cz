---
title: "Analýza řetězců data a času v .NET Frameworku"
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
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6e3ef01abdb615b2850b5a9d07e1208ee22eda95
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analýza řetězců data a času v rozhraní .NET
Analýza metody převést řetězcovou reprezentaci data a času na ekvivalentní <xref:System.DateTime> objektu. <xref:System.DateTime.Parse%2A> a <xref:System.DateTime.TryParse%2A> převádí jakýkoli z několika běžných vyjádření data a času. <xref:System.DateTime.ParseExact%2A> a <xref:System.DateTime.TryParseExact%2A> metody převést řetězcové vyjádření, která vyhovuje vzoru určeného řetězce formátu data a času. (Najdete v tématech na [řetězce formátu standardní hodnoty data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) a [vlastní datum a čas řetězce formátu](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).)  
  
 Analýza je ovlivněna vlastnosti zprostředkovatele formátu, který poskytuje informace, jako jsou třeba řetězce pro datum a čas oddělovačů a názvy měsíců, dnů a období. Zprostředkovatel formátu je aktuální <xref:System.Globalization.DateTimeFormatInfo> objekt, který je poskytnut implicitně aktuální jazykovou verzi vlákna nebo explicitně pomocí <xref:System.IFormatProvider> parametr metody analýzy. Pro <xref:System.IFormatProvider> parametr, zadejte <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objektu.  
  
 Řetězec představující datum ho proto analyzovat musí zahrnovat měsíc a alespoň den nebo rok. Řetězcová reprezentace čas musí zahrnovat hodinu a alespoň minut nebo označení dop. / odp. Ale pokud je to možné analýze poskytne výchozí hodnoty pro vynechané součásti. Chybějící datum nastaveno na aktuální datum, chybějící rok výchozí hodnota je do aktuálního roku, chybějící den měsíce výchozí nastavení, aby první den v měsíci a chybějící čas je nastaven na půlnoc.  
  
 Pokud řetězcová reprezentace určuje pouze čas, analýze vrátí <xref:System.DateTime> objektu s jeho <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, a <xref:System.DateTime.Day%2A> nastaveny na odpovídající hodnoty vlastnosti <xref:System.DateTime.Today%2A> vlastnost. Ale pokud <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> konstanta je uveden v metoda analýzy, výsledná rok, měsíc a den vlastnosti jsou nastaveny na hodnotu `1`.  
  
 Kromě data a času může zahrnovat řetězcovou reprezentaci datum a čas posunem, která určuje, kolik čas se liší od koordinovaný světový čas (UTC). Například řetězec "2/14/2007 5:32:00 -7:00" definuje čas, který je sedm hodin dříve než čas UTC. Pokud je vynechaný posun řetězcovou reprezentaci čas, analýze vrátí <xref:System.DateTime> objektu s jeho <xref:System.DateTime.Kind%2A> vlastnost nastavena na hodnotu <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Pokud je zadaný posun, analýze vrátí <xref:System.DateTime> objektu s jeho <xref:System.DateTime.Kind%2A> vlastnost nastavena na hodnotu <xref:System.DateTimeKind.Local> a jeho hodnota upravena na místní časové pásmo počítače. Toto chování můžete upravit pomocí <xref:System.Globalization.DateTimeStyles> konstantní s metodou analýzy.  
  
 Zprostředkovatel formátu slouží také k interpretaci dvojznačného číselného data. Například není jasné součástí, které data reprezentována řetězec "02/03/04" je měsíc, den a rok. V takovém případě jsou komponenty interpretovány podle pořadí podobné dat. formáty dat v rámci zprostředkovatele formátu.  
  
## <a name="parse"></a>analyzovat  
 Následující příklad kódu ukazuje použití **analyzovat** metoda převést řetězec na **data a času**. Tento příklad používá jazykovou verzi spojenou s aktuální vlákno k provedení analýzy. Pokud <xref:System.Globalization.CultureInfo> přidružené k aktuální jazykovou verzi nelze analyzovat vstupní řetězec <xref:System.FormatException> je vyvolána výjimka.  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 Můžete také zadat **CultureInfo** nastavte na některou z jazykových verzí definovaných prostřednictvím tohoto objektu, nebo můžete nastavit některé standardní <xref:System.Globalization.DateTimeFormatInfo> objektů vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Následující příklad kódu používá formát zprostředkovatele analyzovat řetězec němčině do **data a času**. A **CultureInfo** představující jazykovou verzi, de-DE je definovaný a byla dokončena s řetězec při analýze zajistit úspěšné analýzy tento konkrétní řetězec. To vylučuje jakékoli nastavení **CurrentCulture** z **CurrentThread**.  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 Ale i když můžete použít přetížení metody <xref:System.DateTime.Parse%2A> metodu za účelem určení vlastních poskytovatelů formátu, metoda nepodporuje používání nestandardních poskytovatelů formátu. Chcete-li analyzovat data a času vyjádřené v nestandardním formátu, použijte <xref:System.DateTime.ParseExact%2A> metoda místo.  
  
 Následující příklad kódu používá <xref:System.Globalization.DateTimeStyles> výčtu k určení, že aktuální informace o datu a času nepřidávat **data a času** pro pole, které řetězec nedefinuje.  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact –  
 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Metoda převede řetězec, který odpovídá vzoru zadaný řetězec na **data a času** objektu. Když tato metoda předána řetězec, který není ve tvaru zadaný <xref:System.FormatException> je vyvolána výjimka. Můžete určit jednu standardní datum a čas specifikátory formátu nebo omezenou kombinaci vlastní datum a čas specifikátory formátu. Použití specifikátorů vlastní formátu, je možné sestavit vlastní rozpoznávání řetězec. Informace o specifikátorech, najdete v tématech na [řetězce formátu standardní hodnoty data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) a [vlastní datum a čas řetězce formátu](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).  
  
 Každé přetížení <xref:System.DateTime.ParseExact%2A> metoda má také <xref:System.IFormatProvider> parametr, který obvykle poskytuje informace specifické pro jazykovou verzi o formátování řetězce. Obvykle to <xref:System.IFormatProvider> objekt <xref:System.Globalization.CultureInfo> objekt, který reprezentuje standardní jazykovou verzi nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který je vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Ale na rozdíl od jiných datum a čas funkcí analýzy, tato metoda také podporuje <xref:System.IFormatProvider> nestandardní datum a čas ve formátu, který definuje.  
  
 V následujícím příkladu kódu **ParseExact** metodě se předává objekt string analyzovat, za nímž následuje specifikátorem formátu, za nímž následuje **CultureInfo** objektu. To **ParseExact** metoda analyzovat pouze řetězce, které vykazují vzoru dlouhého data v en US jazykovou verzi.  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
