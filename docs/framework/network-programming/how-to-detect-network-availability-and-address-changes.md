---
title: 'Postupy: zjištění dostupnosti sítě a vyřešení změn'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c0357c4000a7efdb838a40f2f3f907c1dd313c58
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193119"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="691f3-102">Postupy: zjištění dostupnosti sítě a vyřešení změn</span><span class="sxs-lookup"><span data-stu-id="691f3-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="691f3-103">Tento příklad ukazuje, jak zjišťovat změny v adresa síťového rozhraní.</span><span class="sxs-lookup"><span data-stu-id="691f3-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="691f3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="691f3-104">Example</span></span>  
  
```  
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new   
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="691f3-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="691f3-105">Compiling the Code</span></span>  
 <span data-ttu-id="691f3-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="691f3-106">This example requires:</span></span>  
  
-   <span data-ttu-id="691f3-107">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="691f3-107">References to the **System.Net** namespace.</span></span>
