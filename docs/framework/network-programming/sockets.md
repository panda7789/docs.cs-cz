---
title: Sokety
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de5778e398a9a7205e99cc810d0b672ac247da08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sockets"></a><span data-ttu-id="9a47c-102">Sokety</span><span class="sxs-lookup"><span data-stu-id="9a47c-102">Sockets</span></span>
<span data-ttu-id="9a47c-103"><xref:System.Net.Sockets> Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="9a47c-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="9a47c-104">Všechny ostatní-přístup k síti třídy v <xref:System.Net> obor názvů jsou postavená na tuto implementaci soketů.</span><span class="sxs-lookup"><span data-stu-id="9a47c-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="9a47c-105">Rozhraní .NET Framework <xref:System.Net.Sockets.Socket> třída je verzi služby soketu poskytovaný rozhraním Winsock32 API spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9a47c-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="9a47c-106">Ve většině případů **soketu** metody třídy jednoduše zařazování dat do jejich nativní protějšky Win32 a zpracovat všechny kontroly potřeby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9a47c-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="9a47c-107">**Soketu** třída podporuje dva základní režimy synchronní a asynchronní.</span><span class="sxs-lookup"><span data-stu-id="9a47c-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="9a47c-108">V synchronním režimu, zavolá na funkce, které provádějí síťových operací (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A>) počkejte na dokončení operace před vrácením volací program ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9a47c-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="9a47c-109">Tyto volání v asynchronním režimu, vrátí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="9a47c-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a47c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a47c-110">See Also</span></span>  
 [<span data-ttu-id="9a47c-111">Postupy: vytvoření soket</span><span class="sxs-lookup"><span data-stu-id="9a47c-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="9a47c-112">Pomocí protokolů aplikací</span><span class="sxs-lookup"><span data-stu-id="9a47c-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
