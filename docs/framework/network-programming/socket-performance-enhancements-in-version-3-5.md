---
title: Vylepšení výkonu soketů ve verzi 3.5
description: Přečtěte si o vylepšeních výkonu třídy System .NET. Sockets. Socket ve verzi 3,5 v .NET Framework.
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 5a640c58e47bf1630a3a551aed72b9bc9d4fd6fe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502142"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Vylepšení výkonu soketů ve verzi 3.5
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType>Třída byla vylepšena ve verzi 3,5 pro použití aplikacemi, které používají asynchronní vstupně-výstupní operace sítě, aby dosáhly nejvyššího výkonu. Do sady vylepšení třídy byly přidány řady nových tříd <xref:System.Net.Sockets.Socket> , které poskytují alternativní asynchronní vzor, který mohou být použity specializovanými aplikacemi s vysokým výkonem. Tato vylepšení byla navržena speciálně pro aplikace síťového serveru, které vyžadují vysoký výkon. Aplikace může používat rozšířený asynchronní vzorek výhradně nebo pouze v cílových aktivních oblastech své aplikace (například při přijímání velkých objemů dat).  
  
## <a name="class-enhancements"></a>Vylepšení tříd  
 Hlavní funkcí těchto vylepšení je vyhnout se opakovanému přidělení a synchronizaci objektů během vstupně-výstupních asynchronních soketů. Vzor návrhu begin/end, který je aktuálně implementován <xref:System.Net.Sockets.Socket> třídou pro vstupně-výstupní operace asynchronního soketu, vyžaduje <xref:System.IAsyncResult?displayProperty=nameWithType> objekt přidělený pro každou asynchronní operaci soketu.  
  
 V <xref:System.Net.Sockets.Socket> vylepšeních nové třídy jsou operace asynchronního soketu popsány pomocí opakovaně použitelných objektů třídy, které jsou <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> přiděleny a udržovány aplikací. Vysoce výkonné soketové aplikace, které znají nejlepší množství operací překrytých soketů, které musí být trvalé. Aplikace může vytvořit libovolný počet <xref:System.Net.Sockets.SocketAsyncEventArgs> objektů, které potřebuje. Pokud třeba serverová aplikace potřebuje mít po celou dobu nedokončené operace přijetí soketu, aby podporovaly sazby příchozího připojení klientů, může k tomuto účelu přidělit 15 znovu použitelné <xref:System.Net.Sockets.SocketAsyncEventArgs> objekty.  
  
 Vzor pro provedení asynchronní operace soketu s touto třídou se skládá z následujících kroků:  
  
1. Přidělte nový <xref:System.Net.Sockets.SocketAsyncEventArgs> objekt kontextu nebo si z fondu aplikací získejte nějaký bezplatný.  
  
2. Nastavte vlastnosti objektu Context na operaci, která má být provedena (například metoda delegáta zpětného volání a vyrovnávací paměť dat).  
  
3. Pro zahájení asynchronní operace zavolejte příslušnou metodu Socket (xxxAsync).  
  
4. Pokud metoda asynchronního soketu (xxxAsync) vrátí hodnotu true ve zpětném volání, proveďte dotaz na vlastnosti kontextu pro stav dokončení.  
  
5. Pokud metoda asynchronního soketu (xxxAsync) vrátí hodnotu false ve zpětném volání, operace byla dokončena synchronně. Pro výsledek operace lze zadat dotaz na vlastnosti kontextu.  
  
6. Znovu použijte kontext pro jinou operaci, uložte ho do fondu nebo ho zahoďte.  
  
 Životnost nového objektu kontextu asynchronní operace soketu je určena odkazy v kódu aplikace a asynchronních vstupně-výstupních odkazech. Není nutné, aby aplikace zachovala odkaz na objekt kontextu asynchronní operace soketu poté, co byla odeslána jako parametr jedné z metod asynchronní operace soketu. Zůstane odkazováno, dokud zpětné volání dokončení nevrátí. Nicméně je výhodné, aby aplikace zachovala odkaz na objekt kontextu, aby jej bylo možné znovu použít pro budoucí asynchronní operace soketu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Ukázky programování sítě](network-programming-samples.md)
- [Příklady kódu soketu](socket-code-examples.md)
