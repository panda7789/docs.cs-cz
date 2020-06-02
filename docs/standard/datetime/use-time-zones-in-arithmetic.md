---
title: 'Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
ms.openlocfilehash: af19145f7caa9dbe8630ae7593734769e98720d0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280917"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů

Obvykle při provádění aritmetických operací s daty a časem <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnotami neodráží výsledek žádná pravidla upravující časová pásma. To platí i v případě, že časové pásmo hodnoty data a času je jasně identifikovatelné (například když <xref:System.DateTime.Kind%2A> je vlastnost nastavena na hodnotu <xref:System.DateTimeKind.Local> ). V tomto tématu se dozvíte, jak provádět aritmetické operace s hodnotami data a času, které patří do konkrétního časového pásma. Výsledky aritmetických operací budou odrážet pravidla upravující časové pásmo.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Použití pravidel úprav pro aritmetické operace s daty a časem

1. Implementujte některé metody, které budou úzce připojovat hodnotu data a času s časovým pásmem, ke kterému patří. Například deklarujete strukturu, která obsahuje hodnotu data a času a příslušné časové pásmo. Následující příklad používá tento přístup k propojení <xref:System.DateTime> hodnoty s časovým pásmem.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Převeďte čas na koordinovaný světový čas (UTC) voláním <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody nebo <xref:System.TimeZoneInfo.ConvertTime%2A> metody.

3. Proveďte aritmetickou operaci v čase UTC.

4. Převeďte čas z času UTC na původní přiřazené časové pásmo, a to voláním <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.

## <a name="example"></a>Příklad

Následující příklad přidá dvě hodiny a třicet minut do 9. března 2008, v 1:30 dop. Střední oblast (běžný čas) Přechod časového pásma na letní čas probíhá třicet minut později, v 2:00 ráno. 9. března 2008. Vzhledem k tomu, že příklad následuje po čtyřech krocích uvedených v předchozí části, správně oznamuje výsledný čas jako 5:00 dop. 9. března 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<xref:System.DateTime> <xref:System.DateTimeOffset> Z časového pásma, ke kterému by mohly patřit, i hodnoty a jsou odasociovány. Chcete-li provádět aritmetické operace s datem a časem způsobem, který automaticky aplikuje pravidla pro úpravu časového pásma, časové pásmo, do kterého patří jakákoli hodnota data a času, musí být ihned identifikovatelné. To znamená, že datum a čas a jeho přidružené časové pásmo musí být úzce spojeny. To lze provést několika způsoby, mezi které patří následující:

- Předpokládejte, že všechny časy používané v aplikaci patří do konkrétního časového pásma. I když je to v některých případech vhodné, nabízí tento přístup omezená flexibilitu a možnou omezené přenositelnost.

- Definujte typ, který pevně Couples datum a čas s přidruženým časovým pásmem zahrnutím jako polí typu. Tento přístup se používá v příkladu kódu, který definuje strukturu pro uložení data a času a časového pásma do dvou polí členů.

Tento příklad ukazuje, jak provádět aritmetické operace s <xref:System.DateTime> hodnotami, takže pravidla úpravy časového pásma se aplikují na výsledek. Hodnoty však <xref:System.DateTimeOffset> lze použít stejně snadno. Následující příklad ukazuje, jak může být kód v původním příkladu přizpůsoben pro použití <xref:System.DateTimeOffset> namísto <xref:System.DateTime> hodnot.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Všimněte si, že pokud je toto sčítání provedeno na základě <xref:System.DateTimeOffset> hodnoty, aniž byste ji nejprve převedli na čas UTC, výsledek odráží správný bod v čase, ale jeho posun nereflektuje, že určené časové pásmo pro daný čas.

## <a name="compiling-the-code"></a>Zkompilování kódu

Tento příklad vyžaduje:

- Tento <xref:System> obor názvů se naimportuje pomocí `using` příkazu (vyžaduje se v kódu jazyka C#).

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Provádění aritmetických operací s daty a časy](performing-arithmetic-operations.md)
