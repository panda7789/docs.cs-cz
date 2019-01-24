---
title: 'Postupy: Přijímání oznámení o první odpovídající výjimce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed8aaa12e91654dcf0b688b14d7d2f38bc9096ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677737"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Postupy: Přijímání oznámení o první odpovídající výjimce
<xref:System.AppDomain.FirstChanceException> Událost <xref:System.AppDomain> třída umožňuje dostávat oznámení, že byla vyvolána výjimka, před common language runtime začne hledat obslužné rutiny výjimek.

 Událost je vyvolána na úrovni domény aplikace. Vlákno provádění můžete předat prostřednictvím více domén aplikace, takže výjimka je ošetřena v jedné doméně aplikace může být zpracovány v jiné doméně aplikace. Oznámení se vyskytuje v každé doméně aplikace, která se má přidat obslužnou rutinu pro událost, dokud zpracovává výjimku domény aplikace.

 Postupy a příklady v tomto článku ukazují, jak dostávat oznámení o první odpovídající výjimce v jednoduchý program, který má jednu doménu aplikace a v doméně aplikace, kterou vytvoříte.

 Pro složitější příklad, který obsahuje několik domén aplikace, podívejte se na příklad pro <xref:System.AppDomain.FirstChanceException> událostí.

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Příjem oznámení o první odpovídající výjimce ve výchozí doméně aplikace
 V následujícím postupu, vstupní bod pro aplikaci, `Main()` spuštěním metody, ve výchozí doméně aplikace.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>K předvedení oznámení o první odpovídající výjimce ve výchozí doméně aplikace

1.  Definování obslužné rutiny události pro <xref:System.AppDomain.FirstChanceException> událostí, použití výrazu lambda funkce a připojte ho k této události. V tomto příkladu vypisuje obslužná rutina události, název domény aplikace, kde byla zpracována události a výjimky <xref:System.Exception.Message%2A> vlastnost.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2.  Vyvolání výjimky a zachytit. Před běhové prostředí vyhledává obslužnou rutinu výjimky, <xref:System.AppDomain.FirstChanceException> zobrazí zprávu a je vyvolána událost. Tato zpráva je následován zprávu, která se zobrazí při obslužná rutina výjimky.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3.  Vytvořit výjimku, ale nebude zachytávat. Předtím, než modul runtime vyhledá obslužnou rutinu výjimky, <xref:System.AppDomain.FirstChanceException> zobrazí zprávu a je vyvolána událost. Neexistuje žádná obslužná rutina výjimky, takže ukončení aplikace.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     Kód, který se zobrazí v první tři kroky tohoto postupu tvoří úplnou konzolové aplikace. Výstup z aplikace se liší v závislosti na název souboru .exe, protože název výchozí domény aplikace se skládá z názvu a příponu souboru .exe. Si přečtěte následující ukázkový výstup.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Příjem oznámení o první odpovídající výjimce v jiné doméně aplikace
 Pokud váš program obsahuje více než jednu doménu aplikace, můžete nastavit, které domény aplikace přijímat oznámení.

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>K přijímání oznámení o první odpovídající výjimce v doméně aplikace, kterou vytvoříte

1.  Definování obslužné rutiny události <xref:System.AppDomain.FirstChanceException> událostí. Tento příklad používá `static` – metoda (`Shared` metody v jazyce Visual Basic), který vytiskne název domény aplikace, kde byla zpracována události a výjimky <xref:System.Exception.Message%2A> vlastnost.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2.  Vytvoření domény aplikace a přidejme obslužnou rutinu události pro <xref:System.AppDomain.FirstChanceException> události pro tuto doménu aplikace. V tomto příkladu je název domény aplikace `AD1`.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     Tato událost ve výchozí doméně aplikace dokáže zpracovat stejným způsobem. Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastnost `Main()` získat odkaz na výchozí doméně aplikace.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>K předvedení oznámení o první odpovídající výjimce v aplikační doméně

1.  Vytvoření `Worker` objekt v doméně aplikace, kterou jste vytvořili v předchozím postupu. `Worker` Třída musí být veřejné a musí být odvozen od <xref:System.MarshalByRefObject>, jak je uvedeno v úplném příkladu na konci tohoto článku.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2.  Volání metody `Worker` objekt, který vyvolá výjimku. V tomto příkladu `Thrower` metoda je volána dvakrát. První argument metody je `true`, což způsobí, že metoda zachytí vlastní výjimky. Při druhém volání má argument hodnotu `false`a `Main()` metoda zachytí výjimku ve výchozí doméně aplikace.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3.  Kód v umístěte `Thrower` metoda řídit, jestli tato metoda obsluhuje vlastní výjimky.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a>Příklad
 Následující příklad vytvoří aplikační doménu s názvem `AD1` a přidá obslužnou rutinu události do domény aplikace <xref:System.AppDomain.FirstChanceException> událostí. Tento příklad vytvoří instanci `Worker` třídy v aplikační doméně a volá metodu s názvem `Thrower` , které vyvolá <xref:System.ArgumentException>. V závislosti na hodnotě argumentu metody zachytí výjimku nebo selže, aby to zvládnul.

 Pokaždé, když `Thrower` metoda vyvolá výjimku `AD1`, <xref:System.AppDomain.FirstChanceException> událost je aktivována v `AD1`, a zobrazí zprávu, obslužné rutiny události. Modul runtime pak vyhledá obslužnou rutinu výjimky. V prvním případě obslužné rutiny výjimky je nalezena v `AD1`. V druhém případě je neošetřená výjimka v `AD1`a místo toho je zachycena ve výchozí doméně aplikace.

> [!NOTE]
>  Název výchozí domény aplikace je stejný jako název spustitelného souboru.

 Pokud chcete přidat obslužnou rutinu pro <xref:System.AppDomain.FirstChanceException> událostí do výchozí domény aplikace, událost se vyvolá a zpracovány před výchozí domény aplikace zpracovává výjimku. Tento údaj zobrazíte, přidejte kód jazyka C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (v jazyce Visual Basic `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) na začátku `Main()`.

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

-   V tomto příkladu je aplikace příkazového řádku. Chcete-li zkompilovat a spustit tento kód v sadě Visual Studio, přidejte kód jazyka C# `Console.ReadLine();` (v jazyce Visual Basic `Console.ReadLine()`) na konci `Main()`, zabránit ukončit dříve, než si můžete přečíst výstup příkazového okna.

## <a name="see-also"></a>Viz také:
- <xref:System.AppDomain.FirstChanceException>
