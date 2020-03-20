---
title: Vylepšení výkonu soketů ve verzi 3.5
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 577c033fc5639f9d9f50e413fd2cb55a75d48f2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047245"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Vylepšení výkonu soketů ve verzi 3.5
Třída <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> byla vylepšena ve verzi 3.5 pro použití aplikacemi, které používají vstupně-va asynchronní sítě k dosažení nejvyššího výkonu. Řada nových tříd byly přidány jako součást sady vylepšení <xref:System.Net.Sockets.Socket> třídy, které poskytují alternativní asynchronní vzor, který lze použít specializované aplikace s vysokým výkonem soketu. Tato vylepšení byla speciálně navržena pro aplikace síťového serveru, které vyžadují vysoký výkon. Aplikace můžete použít rozšířené asynchronní vzor výhradně nebo pouze v cílových horkých oblastech jejich aplikace (při příjmu velkého množství dat, například).  
  
## <a name="class-enhancements"></a>Vylepšení třídy  
 Hlavním rysem těchto vylepšení je zabránění opakovanému přidělování a synchronizaci objektů během velkoobjemových asynchronních soketů. Počáteční a koncový návrhový vzor <xref:System.Net.Sockets.Socket> aktuálně implementovaný třídou pro vstupně-to asynchronní soket <xref:System.IAsyncResult?displayProperty=nameWithType> vyžaduje, aby byl objekt přidělen pro každou asynchronní operaci soketu.  
  
 V nových <xref:System.Net.Sockets.Socket> vylepšeních třídy jsou asynchronní operace soketu popsány opakovaně použitelnými <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> objekty třídy přidělenými a udržovanými aplikací. Vysoce výkonné aplikace soketu nejlépe znají množství překrývajících se operací soketu, které musí být trvalé. Aplikace může vytvořit tolik <xref:System.Net.Sockets.SocketAsyncEventArgs> objektů, které potřebuje. Například pokud serverová aplikace potřebuje mít 15 soket přijímat operace vynikající po celou dobu pro <xref:System.Net.Sockets.SocketAsyncEventArgs> podporu příchozí sazby připojení klienta, může přidělit 15 opakovaně použitelné objekty předem pro tento účel.  
  
 Vzor pro provádění operace asynchronní soketu s touto třídou se skládá z následujících kroků:  
  
1. Přidělit <xref:System.Net.Sockets.SocketAsyncEventArgs> nový objekt kontextu nebo získat jeden zdarma z fondu aplikací.  
  
2. Nastavte vlastnosti objektu kontextu na operaci, která má být provedena (například metoda delegáta zpětného volání a vyrovnávací paměť dat).  
  
3. Volání příslušné metody soketu (xxxAsync) k zahájení asynchronní operace.  
  
4. Pokud asynchronní socket metoda (xxxAsync) vrátí true v zpětném volání, dotaz vlastnosti kontextu pro dokončení stavu.  
  
5. Pokud asynchronní socket metoda (xxxAsync) vrátí false v zpětném volání, operace dokončena synchronně. Vlastnosti kontextu mohou být dotazovány na výsledek operace.  
  
6. Znovu použít kontext pro jinou operaci, vložte jej zpět do fondu nebo jej zahodit.  
  
 Životnost nového objektu kontextu operace asynchronního soketu je určena odkazy v kódu aplikace a asynchronními vstupně-vaopními odkazy. Není nutné, aby aplikace zachovat odkaz na objekt kontextu operace asynchronní soketu po odeslání jako parametr do jedné z metod operace asynchronní soketu. Zůstane odkazováno, dokud se vrátí zpětná volání dokončení. Je však výhodné pro aplikaci zachovat odkaz na objekt kontextu tak, aby jej lze znovu použít pro budoucí operaci asynchronní soketu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Ukázky programování sítě](network-programming-samples.md)
- [Příklady kódu soketu](socket-code-examples.md)
