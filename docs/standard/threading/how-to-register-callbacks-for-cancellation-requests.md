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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2d61ba254a76235a12ca5dda23fdecb8838ae75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015015"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Postupy: Registrace zpětných volání pro požadavky zrušení
Následující příklad ukazuje, jak zaregistrovat delegáta, který bude vyvolán při <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost stane pravdivou kvůli volání na <xref:System.Threading.CancellationTokenSource.Cancel%2A> na objekt, který vytvoří token. Tento postup použijte pro zrušení asynchronní operace, které nativně nepodporují zrušení jednotné rozhraní framework a pro odblokování metody, které mohou čekat na dokončení asynchronní operace.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech. Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> metoda je zaregistrovaný jako metoda má být volána, když je požadováno zrušení prostřednictvím token zrušení.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Pokud již bylo vyžádáno zrušení při registraci zpětné volání, zpětné volání je stále zaručeně volán. V tomto konkrétním případě <xref:System.Net.WebClient.CancelAsync%2A> metoda neudělá Pokud žádná asynchronní operace probíhá, takže je vždy bezpečné volat metodu.  
  
## <a name="see-also"></a>Viz také:

- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
