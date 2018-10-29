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
ms.openlocfilehash: 3a8e141d79a7f261cd969dc78a656a89ffc8bc30
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196528"
---
# <a name="sockets"></a><span data-ttu-id="ee42e-102">Sokety</span><span class="sxs-lookup"><span data-stu-id="ee42e-102">Sockets</span></span>
<span data-ttu-id="ee42e-103"><xref:System.Net.Sockets> Obor názvů obsahuje spravovanou implementaci rozhraní Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="ee42e-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="ee42e-104">Všechny ostatní – přístup k síti tříd v <xref:System.Net> obor názvů jsou postavené na tuto implementaci soketů.</span><span class="sxs-lookup"><span data-stu-id="ee42e-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="ee42e-105">Rozhraní .NET Framework <xref:System.Net.Sockets.Socket> třídy je verze spravovaného kódu soketu služby poskytované rozhraním Winsock32 API.</span><span class="sxs-lookup"><span data-stu-id="ee42e-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="ee42e-106">Ve většině případů **soketu** metody třídy jednoduše zařazování dat do jejich protějšky nativní Win32 a zpracovat žádné nezbytná bezpečnostní kontroly.</span><span class="sxs-lookup"><span data-stu-id="ee42e-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="ee42e-107">**Soketu** třídy podporuje dva základní způsoby, synchronní a asynchronní.</span><span class="sxs-lookup"><span data-stu-id="ee42e-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="ee42e-108">V synchronním režimu, volání funkce, které provádějí síťových operací (například <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.Receive%2A>) počkejte na dokončení operace před vrácením řízení volající program.</span><span class="sxs-lookup"><span data-stu-id="ee42e-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="ee42e-109">V asynchronním režimu vrátí tato volání okamžitě.</span><span class="sxs-lookup"><span data-stu-id="ee42e-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee42e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee42e-110">See Also</span></span>  
 [<span data-ttu-id="ee42e-111">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="ee42e-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="ee42e-112">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="ee42e-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
