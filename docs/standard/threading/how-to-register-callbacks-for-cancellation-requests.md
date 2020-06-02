---
title: 'Postupy: Registrace zpětných volání pro požadavky zrušení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: 0482d43925f4f547114119a95909501cbf09eedb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279359"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Postupy: Registrace zpětných volání pro požadavky zrušení
Následující příklad ukazuje, jak zaregistrovat delegáta, který bude vyvolán, když se <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost změní na true kvůli volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> na objekt, který vytvořil token. Tuto techniku použijte pro zrušení asynchronních operací, které nativně nepodporují jednotné rozhraní zrušení, a pro odblokování metod, které mohou čekat na dokončení asynchronní operace.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> je metoda registrována jako metoda, která má být vyvolána, když je zrušení požadováno prostřednictvím tokenu zrušení.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Pokud bylo zrušení již vyžádáno při zaregistrování zpětného volání, zpětné volání je stále zaručeno pro volání. V tomto konkrétním případě metoda neprovede <xref:System.Net.WebClient.CancelAsync%2A> žádnou akci, pokud neprobíhá žádná asynchronní operace, takže je vždy bezpečné volat metodu.  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](cancellation-in-managed-threads.md)
