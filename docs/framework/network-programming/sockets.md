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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047260"
---
# <a name="sockets"></a>Sokety
<xref:System.Net.Sockets> Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets. Všechny ostatní třídy přístupu k síti v <xref:System.Net> oboru názvů jsou postaveny nad touto implementací soketů.  
  
 Třída .NET Framework <xref:System.Net.Sockets.Socket> je verze služby soketu spravovaného kódu, kterou poskytuje rozhraní WinSock32 API. Ve většině případů metody třídy **Socket** jednoduše zařazovat data do svých nativních protějšků Win32 a zpracovávají všechny nezbytné kontroly zabezpečení.  
  
 Třída **Socket** podporuje dva základní režimy, synchronní a asynchronní. V synchronním režimu volání funkcí, které provádějí síťové operace (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A>), počkejte na dokončení operace před vrácením řízení volajícímu programu. V asynchronním režimu vrátí tato volání okamžitě.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření soketu](how-to-create-a-socket.md)

- [Použití aplikačních protokolů](using-application-protocols.md)
