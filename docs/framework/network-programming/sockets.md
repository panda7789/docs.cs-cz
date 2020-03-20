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
ms.openlocfilehash: cffad6b4677a880bd63f5ae0232c639f7a262c59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047260"
---
# <a name="sockets"></a>Sokety
Obor <xref:System.Net.Sockets> názvů obsahuje spravovanou implementaci rozhraní Windows Sockets. Všechny ostatní třídy přístupu k síti v oboru <xref:System.Net> názvů jsou postaveny na této implementaci soketů.  
  
 Třída .NET <xref:System.Net.Sockets.Socket> Framework je verze spravovaného kódu soketových služeb poskytovaných rozhraním WINSOCK32 API. Ve většině případů **Socket** metody třídy jednoduše zařazují data do jejich nativní protějšky Win32 a zpracování všech nezbytných kontrol zabezpečení.  
  
 Socket **Socket** Třída podporuje dva základní režimy, synchronní a asynchronní. V synchronním režimu volání funkcí, které provádějí <xref:System.Net.Sockets.Socket.Send%2A> <xref:System.Net.Sockets.Socket.Receive%2A>síťové operace (například a ) počkejte, dokud se operace nedokončí, než vrátíte ovládací prvek volajícímu programu. V asynchronním režimu tato volání okamžitě vrátit.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření soketu](how-to-create-a-socket.md)

- [Použití aplikačních protokolů](using-application-protocols.md)
