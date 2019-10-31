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
ms.openlocfilehash: da60dfca424f7c10e810b5e083ff7fa63a688218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119866"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Postupy: Přijímání oznámení o první odpovídající výjimce
<xref:System.AppDomain.FirstChanceException> událost <xref:System.AppDomain> třídy vám umožní obdržet oznámení o vyvolání výjimky, předtím než modul CLR (Common Language Runtime) začal hledat obslužné rutiny výjimek.

 Událost je vyvolána na úrovni domény aplikace. Vlákno provádění může projít více doménami aplikace, takže výjimka, která je neošetřena v jedné doméně aplikace, by mohla být zpracována v jiné doméně aplikace. K oznámení dojde v každé doméně aplikace, která přidala obslužnou rutinu pro událost, dokud aplikační doména nezpracovává výjimku.

 Postupy a příklady v tomto článku ukazují, jak dostávat oznámení o první pravděpodobné výjimce v jednoduchém programu, který má jednu doménu aplikace, a v doméně aplikace, kterou vytvoříte.

 Složitější příklad, který zahrnuje několik domén aplikace, najdete v příkladu pro událost <xref:System.AppDomain.FirstChanceException>.

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Přijímání oznámení o první odpovídající výjimce ve výchozí doméně aplikace
 V následujícím postupu se vstupní bod pro aplikaci `Main()` Metoda spouští ve výchozí doméně aplikace.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Ukázka oznámení o první odpovídající výjimce ve výchozí doméně aplikace

1. Definujte obslužnou rutinu události pro událost <xref:System.AppDomain.FirstChanceException>, pomocí funkce lambda a připojte ji k události. V tomto příkladu obslužná rutina události vytiskne název domény aplikace, ve které byla událost zpracována, a vlastnost <xref:System.Exception.Message%2A> výjimky.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2. Vyvolejte výjimku a zachyťte ji. Předtím, než modul runtime vyhledá obslužnou rutinu výjimky, je vyvolána událost <xref:System.AppDomain.FirstChanceException> a zobrazí zprávu. Tato zpráva je následována zprávou, která je zobrazena obslužnou rutinou výjimky.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3. Vyvolejte výjimku, ale nezachyťte ji. Předtím, než modul runtime vyhledá obslužnou rutinu výjimky, je vyvolána událost <xref:System.AppDomain.FirstChanceException> a zobrazí zprávu. Není k dispozici obslužná rutina výjimky, takže aplikace se ukončí.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     Kód, který je zobrazen v prvním třech krocích tohoto postupu, tvoří úplnou konzolovou aplikaci. Výstup z aplikace se liší v závislosti na názvu souboru. exe, protože název výchozí domény aplikace se skládá z názvu a přípony souboru. exe. Ukázku výstupu najdete v následujících tématech.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Přijímání oznámení o první pravděpodobné výjimce v jiné doméně aplikace
 Pokud program obsahuje více než jednu doménu aplikace, můžete zvolit, které domény aplikace budou dostávat oznámení.

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Příjem oznámení o první pravděpodobné výjimce v doméně aplikace, kterou vytvoříte

1. Definujte obslužnou rutinu události pro událost <xref:System.AppDomain.FirstChanceException>. Tento příklad používá metodu `static` (`Shared` metoda v Visual Basic), která tiskne název domény aplikace, ve které byla událost zpracována, a vlastnost <xref:System.Exception.Message%2A> výjimky.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2. Vytvořte doménu aplikace a přidejte obslužnou rutinu události do události <xref:System.AppDomain.FirstChanceException> pro danou doménu aplikace. V tomto příkladu je aplikační doména pojmenována `AD1`.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     Tuto událost můžete zpracovat ve výchozí doméně aplikace stejným způsobem. Pomocí vlastnosti `static` (`Shared` in Visual Basic <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>) v `Main()` získat odkaz na výchozí doménu aplikace.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Ukázka oznámení o první pravděpodobnosti v doméně aplikace

1. Vytvořte objekt `Worker` v doméně aplikace, kterou jste vytvořili v předchozím postupu. Třída `Worker` musí být veřejná a musí být odvozena od <xref:System.MarshalByRefObject>, jak je znázorněno v kompletním příkladu na konci tohoto článku.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2. Zavolejte metodu objektu `Worker`, který vyvolá výjimku. V tomto příkladu je metoda `Thrower` volána dvakrát. Poprvé je argument metody `true`, což způsobí, že metoda zachytí svou vlastní výjimku. Druhý čas, argument je `false`a metoda `Main()` zachytí výjimku ve výchozí doméně aplikace.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3. Vložte kód do metody `Thrower` pro řízení, zda metoda zpracovává svou vlastní výjimku.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a>Příklad
 Následující příklad vytvoří doménu aplikace s názvem `AD1` a přidá obslužnou rutinu události do události <xref:System.AppDomain.FirstChanceException> aplikační domény. Příklad vytvoří instanci třídy `Worker` v aplikační doméně a zavolá metodu s názvem `Thrower`, která vyvolá <xref:System.ArgumentException>. V závislosti na hodnotě jeho argumentu Metoda buď zachytí výjimku, nebo ji nedokáže zpracovat.

 Pokaždé, když metoda `Thrower` vyvolá výjimku v `AD1`, událost <xref:System.AppDomain.FirstChanceException> je vyvolána v `AD1`a obslužná rutina události zobrazí zprávu. Modul runtime pak vyhledá obslužnou rutinu výjimky. V prvním případě je obslužná rutina výjimky nalezena v `AD1`. V druhém případě je výjimka neošetřena v `AD1`a místo toho je zachycena ve výchozí doméně aplikace.

> [!NOTE]
> Název výchozí domény aplikace je stejný jako název spustitelného souboru.

 Pokud přidáte obslužnou rutinu pro událost <xref:System.AppDomain.FirstChanceException> do výchozí domény aplikace, událost je vyvolána a zpracována před tím, než výchozí aplikační doména zpracuje výjimku. Pokud to chcete vidět, přidejte C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` kódu (do Visual Basic `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) na začátku `Main()`.

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain.FirstChanceException>
