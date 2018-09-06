---
title: Vylepšení výkonu soketů ve verzi 3.5
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0570241fa81b0870500daa9d6e94b45c28042737
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865111"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Vylepšení výkonu soketů ve verzi 3.5
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Třídy vylepšili jsme ve verzi 3.5 pro použití aplikacemi, které můžete dosáhnout nejvyšší výkon sítě asynchronní vstupně-výstupních operací. Řadu nových tříd se přidaly jako součást sadu rozšíření <xref:System.Net.Sockets.Socket> třídu, která poskytují alternativní asynchronní zpracování, které mohou využívat specializované vysoce výkonné soketu aplikací. Tato vylepšení byly navrženy speciálně pro serverové aplikace sítě, které vyžadují vysoký výkon. Aplikace můžete použít rozšířené asynchronní vzor výhradně, nebo pouze v cílové horké oblastí aplikace (při přijetí velkého objemu dat, třeba).  
  
## <a name="class-enhancements"></a>Třída rozšíření  
 Hlavní funkce tato vylepšení se předcházení opakované přidělení a synchronizace objektů během asynchronního soketu vysoký počet vstupně-výstupních operací. Návrh vzoru Begin/End, v tuto chvíli naimplementované <xref:System.Net.Sockets.Socket> třídy vyžaduje soketu asynchronní vstupně-výstupních operací <xref:System.IAsyncResult?displayProperty=nameWithType> přidělit objekt pro každou asynchronní operace soketu.  
  
 Na novém <xref:System.Net.Sockets.Socket> třídy rozšíření, asynchronní operace jsou popsány pomocí opakovaně použitelného soketu <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> třídy objektů přidělených a spravuje aplikace. Soket vysoce výkonné aplikace nejlíp vědět množství překrývající soketu operace, které musí být zařízením. Aplikace můžete vytvořit tolik z <xref:System.Net.Sockets.SocketAsyncEventArgs> objekty, které potřebuje. Například pokud serverové aplikace musí mít 15 soketu přijmout nevyřízené operace neustále pro podporu příchozí rychlost připojení klienta, jej můžete přidělit 15 opakovaně použitelné <xref:System.Net.Sockets.SocketAsyncEventArgs> objekty předem pro tento účel.  
  
 Vzor pro provádění asynchronní operace soketu se tato třída se skládá z následujících kroků:  
  
1.  Přidělit nový <xref:System.Net.Sockets.SocketAsyncEventArgs> kontextu objektu nebo získejte bezplatné předplatné z fondu aplikací.  
  
2.  Nastavení vlastností pro daný kontext objekt na operaci o bude provedena (zpětné volání delegáta metoda a dat vyrovnávací paměti, například).  
  
3.  Volání metody odpovídající soketu (xxxAsync) k zahájení asynchronní operace.  
  
4.  Pokud metoda asynchronní soketu (xxxAsync) vrací hodnotu true při zpětném volání, dotaz kontextové vlastnosti stav dokončení.  
  
5.  Pokud metoda asynchronní soketu (xxxAsync) vrátí false. zpětné volání, operace se dokončila synchronně. Vlastnosti kontextu může být dotázán na výsledek operace.  
  
6.  Znovu použít kontext pro jiná operace, vložit ho zpátky do fondu nebo zahodit.  
  
 Životnost nový objekt kontextu operace asynchronního soketu se určuje podle odkazů v kódu aplikace a odkazy na asynchronní vstupně-výstupních operací. Není nutné pro aplikaci pro zachování odkaz na objekt kontextu soketu asynchronní operaci po odeslání jako parametr do jedné z metod soketu asynchronní operace. Bude se dál odkazované až do dokončení zpětného volání vrátí. Je ale výhodné pro aplikaci, aby si ponechají odkaz na objekt kontextu, takže můžete znovu použít pro budoucí soketu asynchronní operaci.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Příklady kódu soketu](socket-code-examples.md)
