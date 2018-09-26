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
# <a name="sockets"></a><span data-ttu-id="e6f78-102">Sokety</span><span class="sxs-lookup"><span data-stu-id="e6f78-102">Sockets</span></span>
<span data-ttu-id="e6f78-103"><xref:System.Net.Sockets> Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="e6f78-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="e6f78-104">Všechny ostatní – přístup k síti tříd v <xref:System.Net> obor názvů jsou postavené na tuto implementaci soketů.</span><span class="sxs-lookup"><span data-stu-id="e6f78-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="e6f78-105">Rozhraní .NET Framework <xref:System.Net.Sockets.Socket> třídy je verze spravovaného kódu soketu služby poskytované rozhraním Winsock32 API.</span><span class="sxs-lookup"><span data-stu-id="e6f78-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="e6f78-106">Ve většině případů **soketu** metody třídy jednoduše zařazování dat do jejich protějšky nativní Win32 a zpracovat žádné nezbytná bezpečnostní kontroly.</span><span class="sxs-lookup"><span data-stu-id="e6f78-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="e6f78-107">**Soketu** třídy podporuje dva základní způsoby, synchronní a asynchronní.</span><span class="sxs-lookup"><span data-stu-id="e6f78-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="e6f78-108">V synchronním režimu, volání funkce, které provádějí síťových operací (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A>) počkejte na dokončení operace před vrácením řízení volající program.</span><span class="sxs-lookup"><span data-stu-id="e6f78-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="e6f78-109">V asynchronním režimu vrátí tato volání okamžitě.</span><span class="sxs-lookup"><span data-stu-id="e6f78-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f78-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6f78-110">See Also</span></span>  
 [<span data-ttu-id="e6f78-111">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="e6f78-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="e6f78-112">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="e6f78-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
