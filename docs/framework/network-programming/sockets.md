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
# <a name="sockets"></a><span data-ttu-id="ca0bb-103">Sokety</span><span class="sxs-lookup"><span data-stu-id="ca0bb-103">Sockets</span></span>
<span data-ttu-id="ca0bb-104"><xref:System.Net.Sockets>Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="ca0bb-104">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="ca0bb-105">Všechny ostatní třídy přístupu k síti v <xref:System.Net> oboru názvů jsou postaveny nad touto implementací soketů.</span><span class="sxs-lookup"><span data-stu-id="ca0bb-105">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="ca0bb-106">Třída .NET Framework <xref:System.Net.Sockets.Socket> je verze služby soketu spravovaného kódu, kterou poskytuje rozhraní WinSock32 API.</span><span class="sxs-lookup"><span data-stu-id="ca0bb-106">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="ca0bb-107">Ve většině případů metody třídy **Socket** jednoduše zařazovat data do svých nativních protějšků Win32 a zpracovávají všechny nezbytné kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ca0bb-107">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="ca0bb-108">Třída **Socket** podporuje dva základní režimy, synchronní a asynchronní.</span><span class="sxs-lookup"><span data-stu-id="ca0bb-108">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="ca0bb-109">V synchronním režimu volání funkcí, které provádějí síťové operace (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A> ), počkejte na dokončení operace před vrácením řízení volajícímu programu.</span><span class="sxs-lookup"><span data-stu-id="ca0bb-109">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="ca0bb-110">V asynchronním režimu vrátí tato volání okamžitě.</span><span class="sxs-lookup"><span data-stu-id="ca0bb-110">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0bb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca0bb-111">See also</span></span>

- [<span data-ttu-id="ca0bb-112">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="ca0bb-112">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="ca0bb-113">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="ca0bb-113">Using Application Protocols</span></span>](using-application-protocols.md)
