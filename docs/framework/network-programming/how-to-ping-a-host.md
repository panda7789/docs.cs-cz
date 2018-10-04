---
title: 'Postupy: příkaz Ping na hostitele'
ms.date: 03/30/2017
helpviewer_keywords:
- Ping
ms.assetid: bbf20f5b-eca1-4661-af04-cb8837f9af05
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e066af175982b71fb42bf2eec75fe9d92f532e61
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48264381"
---
# <a name="how-to-ping-a-host"></a><span data-ttu-id="04654-102">Postupy: příkaz Ping na hostitele</span><span class="sxs-lookup"><span data-stu-id="04654-102">How to: Ping a Host</span></span>
<span data-ttu-id="04654-103">Tento příklad ukazuje, jak pomocí příkazu ping vzdálený hostitel.</span><span class="sxs-lookup"><span data-stu-id="04654-103">This sample shows how to ping a remote host.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04654-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="04654-104">Example</span></span>  
  
```  
using System;  
using System.Text;  
using System.Net;  
using System.Net.NetworkInformation;  
using System.ComponentModel;  
using System.Threading;  
  
namespace Examples.System.Net.NetworkInformation.PingTest  
{  
    public class PingExample  
    {  
        public static void Main (string[] args)  
        {  
            if (args.Length == 0)  
                throw new ArgumentException ("Ping needs a host or IP Address.");  
  
            string who = args[0];  
            AutoResetEvent waiter = new AutoResetEvent (false);  
  
            Ping pingSender = new Ping ();  
  
            // When the PingCompleted event is raised,  
            // the PingCompletedCallback method is called.  
            pingSender.PingCompleted += new PingCompletedEventHandler (PingCompletedCallback);  
  
            // Create a buffer of 32 bytes of data to be transmitted.  
            string data = "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";  
            byte[] buffer = Encoding.ASCII.GetBytes (data);  
  
            // Wait 12 seconds for a reply.  
            int timeout = 12000;  
  
            // Set options for transmission:  
            // The data can go through 64 gateways or routers  
            // before it is destroyed, and the data packet  
            // cannot be fragmented.  
            PingOptions options = new PingOptions (64, true);  
  
            Console.WriteLine ("Time to live: {0}", options.Ttl);  
            Console.WriteLine ("Don't fragment: {0}", options.DontFragment);  
  
            // Send the ping asynchronously.  
            // Use the waiter as the user token.  
            // When the callback completes, it can wake up this thread.  
            pingSender.SendAsync(who, timeout, buffer, options, waiter);  
  
            // Prevent this example application from ending.  
            // A real application should do something useful  
            // when possible.  
            waiter.WaitOne ();  
            Console.WriteLine ("Ping example completed.");  
        }  
  
        public static void PingCompletedCallback (object sender, PingCompletedEventArgs e)  
        {  
            // If the operation was canceled, display a message to the user.  
            if (e.Cancelled)  
            {  
                Console.WriteLine ("Ping canceled.");  
  
                // Let the main thread resume.   
                // UserToken is the AutoResetEvent object that the main thread   
                // is waiting for.  
                ((AutoResetEvent)e.UserState).Set ();  
            }  
  
            // If an error occurred, display the exception to the user.  
            if (e.Error != null)  
            {  
                Console.WriteLine ("Ping failed:");  
                Console.WriteLine (e.Error.ToString ());  
  
                // Let the main thread resume.   
                ((AutoResetEvent)e.UserState).Set();  
            }  
  
            PingReply reply = e.Reply;  
  
            DisplayReply (reply);  
  
            // Let the main thread resume.  
            ((AutoResetEvent)e.UserState).Set();  
        }  
  
        public static void DisplayReply (PingReply reply)  
        {  
            if (reply == null)  
                return;  
  
            Console.WriteLine ("ping status: {0}", reply.Status);  
            if (reply.Status == IPStatus.Success)  
            {  
                Console.WriteLine ("Address: {0}", reply.Address.ToString ());  
                Console.WriteLine ("RoundTrip time: {0}", reply.RoundtripTime);  
                Console.WriteLine ("Time to live: {0}", reply.Options.Ttl);  
                Console.WriteLine ("Don't fragment: {0}", reply.Options.DontFragment);  
                Console.WriteLine ("Buffer size: {0}", reply.Buffer.Length);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="04654-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="04654-105">Compiling the Code</span></span>  
 <span data-ttu-id="04654-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="04654-106">This example requires:</span></span>  
  
-   <span data-ttu-id="04654-107">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="04654-107">References to the **System.Net** namespace.</span></span>
