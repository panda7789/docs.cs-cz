---
title: Vylepšení výkonu soketu v verze 3.5
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db52123167648744141657d885f3d3dcc524dd3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="socket-performance-enhancements-in-version-35"></a>Vylepšení výkonu soketu v verze 3.5
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Třída je vylepšená v verze 3.5 pro použití aplikací, které používají vstupně-výstupní operace asynchronní sítě k dosažení nejvyšší výkon. Řadu nové třídy přidané jako součást sadu vylepšení <xref:System.Net.Sockets.Socket> třídu, která poskytují alternativní asynchronní vzor, který lze použít speciální soketu vysoce výkonné aplikace. Tato vylepšení byly navrženy speciálně pro serverové aplikace sítě, které vyžadují vysoký výkon. Aplikace můžete použít rozšířené asynchronní vzor výhradně, nebo pouze v cílové aktivní oblasti jejich aplikace (při přijímání velkého objemu dat, například).  
  
## <a name="class-enhancements"></a>Vylepšení – třída  
 Hlavní funkce tato vylepšení je předcházení opakované přidělení a synchronizace objektů během asynchronní soketu vysoký počet vstupně-výstupní operace. Vzor návrhu začátek/konec aktuálně implementované <xref:System.Net.Sockets.Socket> třídy pro vyžaduje soketu asynchronní vstupně-výstupních operací <xref:System.IAsyncResult?displayProperty=nameWithType> přidělit objekt pro každou operaci asynchronní soketu.  
  
 V novém <xref:System.Net.Sockets.Socket> třídy vylepšení, asynchronní soketu operace jsou popsány podle opakovaně použitelného <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> třídy objekty přidělené a udržované pomocí aplikace. Socket vysoce výkonné aplikace znát nejlépe množství překryté soketu operace, které musí být zařízením. Aplikace můžete vytvořit jako řadu <xref:System.Net.Sockets.SocketAsyncEventArgs> objekty, které potřebuje. Například pokud je serverová aplikace musí mít 15 soketu přijmout operace nezpracovaných kdykoli podporují příchozí rychlosti připojení klienta, ho můžete přidělit 15 opakovaně použitelné <xref:System.Net.Sockets.SocketAsyncEventArgs> objekty předem k tomuto účelu.  
  
 Vzor pro provádění operace asynchronní soketu s touto třídou se skládá z následujících kroků:  
  
1.  Přidělit nový <xref:System.Net.Sockets.SocketAsyncEventArgs> kontextu objektu nebo získat volné jeden z fondu aplikací.  
  
2.  Umožňuje nastavit vlastnosti v kontextu objektu k operaci o být provést (zpětné volání delegáta metoda a data vyrovnávací paměti, např.).  
  
3.  Volání metody odpovídající soketů (xxxAsync) inicializace asynchronní operace.  
  
4.  Pokud metoda asynchronní soketů (xxxAsync), vrátí hodnotu true v zpětné volání, dotaz vlastností kontextu pro stav dokončení.  
  
5.  Pokud metoda asynchronní soketů (xxxAsync), vrátí hodnotu false v zpětné volání, operace byla dokončena synchronně. Vlastností kontextu může být dotázán na výsledek operace.  
  
6.  Znovu použít kontext pro jiná operace, dejte ho zpět do fondu nebo ji zrušit.  
  
 Životnost nový objekt kontextu operace asynchronní soketu je určen podle odkazy v kódu aplikace a odkazy na asynchronní vstupně-výstupní operace. Není nutné pro aplikace, které chcete zachovat odkaz na objekt soketu asynchronní operaci kontextu po odeslání jako parametr pro jednu z metod operace asynchronní soketu. Zůstává odkazované až do dokončení zpětného volání vrátí. Ale je výhodné pro aplikaci chcete zachovat odkaz na objekt context tak, aby lze znovu použít pro budoucí soketu asynchronní operaci.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázka technologie soketu výkonu](http://go.microsoft.com/fwlink/?LinkID=179570)
