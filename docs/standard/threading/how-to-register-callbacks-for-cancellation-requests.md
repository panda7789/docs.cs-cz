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
ms.openlocfilehash: 87ba1ab9ac095c733a53f766d00ebb7530a8d9c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138002"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Postupy: Registrace zpětných volání pro požadavky zrušení
Následující příklad ukazuje, jak zaregistrovat delegáta, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> který bude vyvolán, když <xref:System.Threading.CancellationTokenSource.Cancel%2A> se vlastnost stane true z důvodu volání na objekt, který vytvořil token. Tento postup použijte pro zrušení asynchronních operací, které nativně nepodporují sjednocené rozhraní pro zrušení, a pro odblokovací metody, které mohou čekat na dokončení asynchronní operace.  
  
> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže. Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> je metoda registrována jako metoda, která má být vyvolána při požadavku na zrušení prostřednictvím tokenu zrušení.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Pokud zrušení již byla požadována při zpětnévolání je registrována, zpětné volání je stále zaručeno, že bude volána. V tomto konkrétním <xref:System.Net.WebClient.CancelAsync%2A> případě metoda nebude dělat nic, pokud probíhá žádná asynchronní operace, takže je vždy bezpečné volat metodu.  
  
## <a name="see-also"></a>Viz také

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
