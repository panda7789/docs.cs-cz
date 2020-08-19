---
title: Registrace zpětných volání pro žádosti o zrušení
ms.date: 08/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: faa8dada5779f6eaee7a60e6210ec604f5fb4680
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608457"
---
# <a name="register-callbacks-for-cancellation-requests"></a>Registrace zpětných volání pro žádosti o zrušení

Naučte se, jak zaregistrovat delegáta, který se vyvolá, když se <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost změní na true. Hodnota se změní z false na true, pokud <xref:System.Threading.CancellationTokenSource.Cancel%2A> je provedeno volání na objekt, který vytvořil token. Tuto techniku použijte pro zrušení asynchronních operací, které nativně nepodporují jednotné rozhraní zrušení, a pro odblokování metod, které mohou čekat na dokončení asynchronní operace.

> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Stiskem klávesy <kbd>F5</kbd> můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.

## <a name="example"></a>Příklad

V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> je metoda registrována jako metoda, která má být vyvolána, když je zrušení požadováno prostřednictvím tokenu zrušení.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

Pokud bylo zrušení již vyžádáno při zaregistrování zpětného volání, zpětné volání je stále zaručeno pro volání. V tomto konkrétním případě metoda neprovede <xref:System.Net.WebClient.CancelAsync%2A> žádnou akci, pokud neprobíhá žádná asynchronní operace, takže je vždy bezpečné volat metodu.

## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
