---
title: Interpretace trasování sítě
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: fd617e152b1e86cc71dd8e3cc8a01f1d2f52c30a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047894"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="829dd-102">Interpretace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="829dd-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="829dd-103">Pokud je povoleno trasování sítě, můžete použít trasování k zaznamenání volání, která vaše aplikace <xref:System.Net> předává různým členům třídy.</span><span class="sxs-lookup"><span data-stu-id="829dd-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="829dd-104">Výstup z těchto volání může být podobný jako v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="829dd-104">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="829dd-105">V předchozím příkladu je [588] jedinečný identifikátor aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="829dd-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="829dd-106">(4357) a (4387) jsou časová razítka označující počet milisekund, které uplynuly od spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="829dd-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="829dd-107">Data následující za časovým razítkem zobrazí aplikaci, která zadává a ukončuje metodu **Socket. Send**.</span><span class="sxs-lookup"><span data-stu-id="829dd-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="829dd-108">Objekt, který spouští metodu **Send** , má jako jedinečný identifikátor 33574638.</span><span class="sxs-lookup"><span data-stu-id="829dd-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="829dd-109">Metoda Exit Trace zahrnuje návratovou hodnotu (61 v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="829dd-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="829dd-110">Trasování sítě mohou zachytit síťový provoz, který je odesílán nebo přijat vaší aplikací pomocí protokolů na úrovni aplikace, jako je protokol HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="829dd-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="829dd-111">Tato data se můžou zachytit jako text a volitelně také hexadecimální data.</span><span class="sxs-lookup"><span data-stu-id="829dd-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="829dd-112">Šestnáctková data jsou k dispozici při zadání **includehex** jako hodnoty atributu **TraceMode** .</span><span class="sxs-lookup"><span data-stu-id="829dd-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="829dd-113">(Podrobné informace o tomto atributu naleznete v tématu [How to: Konfigurace trasování](how-to-configure-network-tracing.md)sítě.) Následující příklad trasování byl vygenerován pomocí **includehex**.</span><span class="sxs-lookup"><span data-stu-id="829dd-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="829dd-114">Chcete-li vynechat šestnáctková data, zadejte **protocolonly** jako hodnotu pro atribut **TraceMode** .</span><span class="sxs-lookup"><span data-stu-id="829dd-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="829dd-115">Následující příklad ukazuje trasování při zadání **protocolonly** .</span><span class="sxs-lookup"><span data-stu-id="829dd-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="829dd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="829dd-116">See also</span></span>

- [<span data-ttu-id="829dd-117">Povolení trasování sítě</span><span class="sxs-lookup"><span data-stu-id="829dd-117">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="829dd-118">Postupy: Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="829dd-118">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="829dd-119">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="829dd-119">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
