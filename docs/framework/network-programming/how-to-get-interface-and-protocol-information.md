---
title: 'Postupy: Získání informace o rozhraní a protokolu'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: fd88d26c-4063-495e-a253-736ac3e6b23f
ms.openlocfilehash: 231d658cf13d27936b7b362ef8b4ccad78614b73
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894723"
---
# <a name="how-to-get-interface-and-protocol-information"></a><span data-ttu-id="f8b05-102">Postupy: Získání informace o rozhraní a protokolu</span><span class="sxs-lookup"><span data-stu-id="f8b05-102">How to: Get Interface and Protocol Information</span></span>
<span data-ttu-id="f8b05-103">V této ukázce se dozvíte, jak přečíst statistiku protokolu TCP síťového rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8b05-103">This sample shows how to read the TCP statistics of a network interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8b05-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8b05-104">Example</span></span>  
  
```csharp
public static void ShowTcpStatistics(NetworkInterfaceComponent version)  
{  
    IPGlobalProperties properties =  
          IPGlobalProperties.GetIPGlobalProperties();  
    TcpStatistics tcpstat = null;  
    Console.WriteLine("");  
    switch (version)  
    {  
        case NetworkInterfaceComponent.IPv4:  
             tcpstat = properties.GetTcpIPv4Statistics();  
            Console.WriteLine("TCP/IPv4 Statistics:");  
            break;  
        case NetworkInterfaceComponent.IPv6:  
            tcpstat = properties.GetTcpIPv6Statistics();  
            Console.WriteLine("TCP/IPv6 Statistics:");  
            break;  
        default:  
            throw new ArgumentException("version");  
            break;  
    }  
    Console.WriteLine("  Minimum Transmission Timeout. : {0}",   
        tcpstat.MinimumTransmissionTimeout);  
    Console.WriteLine("  Maximum Transmission Timeout. : {0}",   
        tcpstat.MaximumTransmissionTimeout);  
  
    Console.WriteLine("  Connection Data:");  
    Console.WriteLine("      Current : {0}",   
    tcpstat.CurrentConnections);  
    Console.WriteLine("      Cumulative : {0}",   
        tcpstat.CumulativeConnections);  
    Console.WriteLine("      Initiated  : {0}",   
        tcpstat.ConnectionsInitiated);  
    Console.WriteLine("      Accepted : {0}",   
        tcpstat.ConnectionsAccepted);  
    Console.WriteLine("      Failed Attempts : {0}",   
        tcpstat.FailedConnectionAttempts);  
    Console.WriteLine("      Reset : {0}",   
        tcpstat.ResetConnections);  
  
    Console.WriteLine("");  
    Console.WriteLine("  Segment Data:");  
    Console.WriteLine("      Received  ................... : {0}",   
        tcpstat.SegmentsReceived);  
    Console.WriteLine("      Sent : {0}",   
        tcpstat.SegmentsSent);  
    Console.WriteLine("      Retransmitted : {0}",   
        tcpstat.SegmentsResent);  
  
    Console.WriteLine("");  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8b05-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f8b05-105">Compiling the Code</span></span>  
 <span data-ttu-id="f8b05-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f8b05-106">This example requires:</span></span>  
  
- <span data-ttu-id="f8b05-107">Odkazuje na obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="f8b05-107">References to the **System.Net** namespace.</span></span>
