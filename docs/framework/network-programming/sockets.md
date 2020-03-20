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
# <a name="sockets"></a><span data-ttu-id="6b9f1-102">Sokety</span><span class="sxs-lookup"><span data-stu-id="6b9f1-102">Sockets</span></span>
<span data-ttu-id="6b9f1-103">Obor <xref:System.Net.Sockets> názvů obsahuje spravovanou implementaci rozhraní Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="6b9f1-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="6b9f1-104">Všechny ostatní třídy přístupu k síti v oboru <xref:System.Net> názvů jsou postaveny na této implementaci soketů.</span><span class="sxs-lookup"><span data-stu-id="6b9f1-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="6b9f1-105">Třída .NET <xref:System.Net.Sockets.Socket> Framework je verze spravovaného kódu soketových služeb poskytovaných rozhraním WINSOCK32 API.</span><span class="sxs-lookup"><span data-stu-id="6b9f1-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="6b9f1-106">Ve většině případů **Socket** metody třídy jednoduše zařazují data do jejich nativní protějšky Win32 a zpracování všech nezbytných kontrol zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6b9f1-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="6b9f1-107">Socket **Socket** Třída podporuje dva základní režimy, synchronní a asynchronní.</span><span class="sxs-lookup"><span data-stu-id="6b9f1-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="6b9f1-108">V synchronním režimu volání funkcí, které provádějí <xref:System.Net.Sockets.Socket.Send%2A> <xref:System.Net.Sockets.Socket.Receive%2A>síťové operace (například a ) počkejte, dokud se operace nedokončí, než vrátíte ovládací prvek volajícímu programu.</span><span class="sxs-lookup"><span data-stu-id="6b9f1-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="6b9f1-109">V asynchronním režimu tato volání okamžitě vrátit.</span><span class="sxs-lookup"><span data-stu-id="6b9f1-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9f1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b9f1-110">See also</span></span>

- [<span data-ttu-id="6b9f1-111">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="6b9f1-111">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="6b9f1-112">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="6b9f1-112">Using Application Protocols</span></span>](using-application-protocols.md)
