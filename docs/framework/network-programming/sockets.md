---
title: Sokety
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ce7ded81ad23c2df55afa9360435e8391fea7a63
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176822"
---
# <a name="sockets"></a>Sokety
<xref:System.Net.Sockets> Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets. Všechny ostatní – přístup k síti tříd v <xref:System.Net> obor názvů jsou postavené na tuto implementaci soketů.  
  
 Rozhraní .NET Framework <xref:System.Net.Sockets.Socket> třídy je verze spravovaného kódu soketu služby poskytované rozhraním Winsock32 API. Ve většině případů **soketu** metody třídy jednoduše zařazování dat do jejich protějšky nativní Win32 a zpracovat žádné nezbytná bezpečnostní kontroly.  
  
 **Soketu** třídy podporuje dva základní způsoby, synchronní a asynchronní. V synchronním režimu, volání funkce, které provádějí síťových operací (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A>) počkejte na dokončení operace před vrácením řízení volající program. V asynchronním režimu vrátí tato volání okamžitě.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření soketu](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)
