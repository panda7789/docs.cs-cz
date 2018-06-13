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
ms.openlocfilehash: d48aa2029d11c884b81aa5181845e71b2756d629
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744366"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Postupy: Přijímání oznámení o první odpovídající výjimce
<xref:System.AppDomain.FirstChanceException> Události <xref:System.AppDomain> třída umožňuje přijímat oznámení, že byla vyvolána výjimka, před common language runtime začne hledat obslužné rutiny výjimek.  
  
 Událost se vyvolá na úrovni domény aplikace. Podproces provádění mohou procházet několik domén aplikace, tak v jiné doméně aplikace může zpracovávat výjimka, která je neošetřená v jedné doméně aplikace. Oznámení dochází v každé doméně aplikace, který byl přidán obslužnou rutinu události, dokud doménu aplikace ošetří výjimku.  
  
 Postupy a příklady v tomto článku ukazují, jak dostávat oznámení o první odpovídající výjimce v jednoduchý program, který má jednu doménu aplikace a v doméně aplikace, který vytvoříte.  
  
 Složitější příklad, který obsahuje několik domén aplikace, podívejte se příklad <xref:System.AppDomain.FirstChanceException> událostí.  
  
## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Příjem oznámení první odpovídající výjimce ve výchozí doméně aplikace  
 V následujícím postupu, vstupní bod pro aplikaci `Main()` metoda, běží ve výchozí doméně aplikace.  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>K předvedení první odpovídající výjimce oznámení ve výchozí doméně aplikace  
  
1.  Definování obslužné rutiny události pro <xref:System.AppDomain.FirstChanceException> událost, pomocí lambda funkce a připojte ji k události. V tomto příkladu obslužné rutiny události vytiskne název domény aplikace, kde byla zpracována událost a v výjimky <xref:System.Exception.Message%2A> vlastnost.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]  
  
2.  Způsobí výjimku a zachyťte ji. Před běhové prostředí vyhledává obslužná rutina výjimky <xref:System.AppDomain.FirstChanceException> zobrazí zprávu a je vyvolána událost. Tato zpráva je následován zprávu, která se zobrazí při obslužná rutina výjimky.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]  
  
3.  Způsobí výjimku, ale není catch. Před běhové prostředí vyhledává obslužné rutiny výjimky <xref:System.AppDomain.FirstChanceException> událost se vyvolá a zobrazí zprávu. Neexistuje žádná obslužná rutina výjimky, takže aplikace se ukončí.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]  
  
     Kód, který se zobrazí v první tři kroky tohoto postupu, tvoří úplnou konzolové aplikace. Výstup z aplikace se liší v závislosti na název souboru .exe, protože název výchozí doméně aplikace se skládá z název a příponu souboru .exe. Viz následující ukázka výstupu.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]  
  
## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Příjem oznámení první odpovídající výjimce v jiné doméně aplikace  
 Pokud váš program obsahuje více než jednu doménu aplikace, můžete vybrat, které aplikační domény přijímat oznámení.  
  
#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Pro příjem oznámení první odpovídající výjimce v doméně aplikace, kterou vytvoříte  
  
1.  Definování obslužné rutiny události pro <xref:System.AppDomain.FirstChanceException> událostí. Tento příklad používá `static` – metoda (`Shared` metody v jazyce Visual Basic), vytiskne název domény aplikace, kde byla zpracována událost a v výjimky <xref:System.Exception.Message%2A> vlastnost.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]  
  
2.  Vytvoření domény aplikace a přidejte obslužné rutiny události pro <xref:System.AppDomain.FirstChanceException> události pro tuto doménu aplikace. V tomto příkladu je název domény aplikace `AD1`.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]  
  
     Tato událost ve výchozí doméně aplikace můžete zpracovat stejným způsobem. Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastnost `Main()` získat odkaz na výchozí doméně aplikace.  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>K předvedení první odpovídající výjimce oznámení v doméně aplikace  
  
1.  Vytvoření `Worker` objekt v doméně aplikace, kterou jste vytvořili v předchozím postupu. `Worker` Třídy musí být veřejná a musí být odvozeny od <xref:System.MarshalByRefObject>, jak je znázorněno v příkladu na konci tohoto článku.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]  
  
2.  Volání metody `Worker` objekt, který vyvolá výjimku. V tomto příkladu `Thrower` metoda je volána dvakrát. První argument metoda je `true`, což způsobí, že metoda zachytí svou vlastní výjimku. Při druhém argument je `false`a `Main()` metoda zachytí výjimky ve výchozí doméně aplikace.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]  
  
3.  Umístěte kód `Thrower` metoda řídit, jestli tato metoda obsluhuje svou vlastní výjimku.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří doménu aplikace s názvem `AD1` a přidá obslužné rutiny události do domény aplikace <xref:System.AppDomain.FirstChanceException> událostí. V příkladu se vytváří instance `Worker` třídy v doméně aplikace a volá metodu pojmenovanou `Thrower` , vyvolá <xref:System.ArgumentException>. V závislosti na hodnotě argumentu metoda buď zachytí výjimky, nebo selže se nezdařilo.  
  
 Pokaždé, když `Thrower` metoda vyvolá výjimku `AD1`, <xref:System.AppDomain.FirstChanceException> událost se vyvolá v `AD1`, a zobrazí zprávu, obslužné rutiny události. Modul runtime pak hledá obslužnou rutinu výjimky. V prvním případě je obslužná rutina výjimky nalezena v `AD1`. V druhém případě je výjimka ošetřena v `AD1`a místo toho je zachycena ve výchozí doméně aplikace.  
  
> [!NOTE]
>  Název výchozí doméně aplikace je stejný jako název spustitelného souboru.  
  
 Pokud přidáte obslužnou rutinu pro <xref:System.AppDomain.FirstChanceException> je událost, která má výchozí doménu aplikace, událost vyvolána a zpracovává než výchozí doméně aplikace ošetří výjimku. Chcete-li najdete v článku, přidejte kód C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (v jazyce Visual Basic `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) na začátku `Main()`.  
  
 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   V tomto příkladu je aplikace příkazového řádku. Pro zkompilování a spuštění tohoto kódu [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], přidejte kód C# `Console.ReadLine();` (v jazyce Visual Basic `Console.ReadLine()`) na konci `Main()`, aby se zabránilo příkazové okno Ukončit předtím, než si můžete přečíst výstup.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppDomain.FirstChanceException>
