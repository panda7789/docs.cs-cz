---
title: Vylepšení výkonu soketů ve verzi 3.5
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 577c033fc5639f9d9f50e413fd2cb55a75d48f2c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047245"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Vylepšení výkonu soketů ve verzi 3.5
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Třída byla vylepšena ve verzi 3,5 pro použití aplikacemi, které používají asynchronní vstupně-výstupní operace sítě, aby dosáhly nejvyššího výkonu. Do sady vylepšení <xref:System.Net.Sockets.Socket> třídy byly přidány řady nových tříd, které poskytují alternativní asynchronní vzor, který mohou být použity specializovanými aplikacemi s vysokým výkonem. Tato vylepšení byla navržena speciálně pro aplikace síťového serveru, které vyžadují vysoký výkon. Aplikace může používat rozšířený asynchronní vzorek výhradně nebo pouze v cílových aktivních oblastech své aplikace (například při přijímání velkých objemů dat).  
  
## <a name="class-enhancements"></a>Vylepšení tříd  
 Hlavní funkcí těchto vylepšení je vyhnout se opakovanému přidělení a synchronizaci objektů během vstupně-výstupních asynchronních soketů. Vzor návrhu begin/end, který je <xref:System.Net.Sockets.Socket> aktuálně implementován třídou pro vstupně-výstupní operace asynchronního soketu, <xref:System.IAsyncResult?displayProperty=nameWithType> vyžaduje objekt přidělený pro každou asynchronní operaci soketu.  
  
 V vylepšeních <xref:System.Net.Sockets.Socket> nové třídy jsou operace asynchronního soketu popsány <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> pomocí opakovaně použitelných objektů třídy, které jsou přiděleny a udržovány aplikací. Vysoce výkonné soketové aplikace, které znají nejlepší množství operací překrytých soketů, které musí být trvalé. Aplikace může vytvořit libovolný <xref:System.Net.Sockets.SocketAsyncEventArgs> počet objektů, které potřebuje. Pokud třeba serverová aplikace potřebuje mít po celou dobu nedokončené operace přijetí soketu, aby podporovaly sazby příchozího připojení klientů, může k tomuto účelu <xref:System.Net.Sockets.SocketAsyncEventArgs> přidělit 15 znovu použitelné objekty.  
  
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
