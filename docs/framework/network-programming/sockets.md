---
title: Sokety
description: Přečtěte si o třídách soketu .NET Framework, což je verze služby soketu spravovaného kódu, kterou poskytuje rozhraní API pro WinSock32.
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
ms.openlocfilehash: b44409a0fafc770625be55881ccef3b57045acef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502129"
---
# <a name="sockets"></a>Sokety
<xref:System.Net.Sockets>Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets. Všechny ostatní třídy přístupu k síti v <xref:System.Net> oboru názvů jsou postaveny nad touto implementací soketů.  
  
 Třída .NET Framework <xref:System.Net.Sockets.Socket> je verze služby soketu spravovaného kódu, kterou poskytuje rozhraní WinSock32 API. Ve většině případů metody třídy **Socket** jednoduše zařazovat data do svých nativních protějšků Win32 a zpracovávají všechny nezbytné kontroly zabezpečení.  
  
 Třída **Socket** podporuje dva základní režimy, synchronní a asynchronní. V synchronním režimu volání funkcí, které provádějí síťové operace (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A> ), počkejte na dokončení operace před vrácením řízení volajícímu programu. V asynchronním režimu vrátí tato volání okamžitě.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření soketu](how-to-create-a-socket.md)

- [Použití aplikačních protokolů](using-application-protocols.md)
