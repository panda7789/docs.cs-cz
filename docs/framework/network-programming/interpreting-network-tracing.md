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
ms.openlocfilehash: 94a64efcd7b4f354eaa22d1b646f36212f9c8fbb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152253"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="ce83e-102">Interpretace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="ce83e-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="ce83e-103">Pokud je povoleno trasování sítě, můžete použít trasování pro zachycení volání, které vaše aplikace odešle do různých <xref:System.Net> členy třídy.</span><span class="sxs-lookup"><span data-stu-id="ce83e-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="ce83e-104">Výstup z těchto volání může být podobně jako v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="ce83e-104">The output from these calls may be similar to the following examples.</span></span>  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 <span data-ttu-id="ce83e-105">V předchozím příkladu [588] je jedinečný identifikátor aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="ce83e-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="ce83e-106">(4357) a (4387) jsou časové razítko označující počet milisekund uplynulých od spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce83e-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="ce83e-107">Data po časové razítko je vidět aplikace vstupující do a vystupující metodu **Socket.Send**.</span><span class="sxs-lookup"><span data-stu-id="ce83e-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="ce83e-108">Objekt provádění **odeslat** metoda má 33574638 jako svůj jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="ce83e-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="ce83e-109">Trasování ukončovací metoda zahrnuje návratovou hodnotu (61 v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="ce83e-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="ce83e-110">Trasování sítě můžete zaznamenávat síťový provoz, který je odeslaných nebo přijatých aplikací pomocí protokolů úrovni aplikace, jako je protokol HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="ce83e-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="ce83e-111">Tato data se dají zachytit jako text a volitelně data v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="ce83e-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="ce83e-112">Šestnáctkové data jsou k dispozici, když zadáte **includehex** jako hodnotu **tracemode** atribut.</span><span class="sxs-lookup"><span data-stu-id="ce83e-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="ce83e-113">(Podrobné informace o tomto atributu naleznete v tématu [jak: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) Následující příklad trasování se vygeneroval pomocí **includehex**.</span><span class="sxs-lookup"><span data-stu-id="ce83e-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="ce83e-114">Pokud chcete vynechat, nechte šestnáctkových dat., zadejte **protocolonly** hodnotu **tracemode** atribut.</span><span class="sxs-lookup"><span data-stu-id="ce83e-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="ce83e-115">Následující příklad ukazuje trasování při **protocolonly** určena.</span><span class="sxs-lookup"><span data-stu-id="ce83e-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="ce83e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce83e-116">See Also</span></span>  
 [<span data-ttu-id="ce83e-117">Povolení trasování sítě</span><span class="sxs-lookup"><span data-stu-id="ce83e-117">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [<span data-ttu-id="ce83e-118">Jak: Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="ce83e-118">How to: Configure Network Tracing</span></span>](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [<span data-ttu-id="ce83e-119">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce83e-119">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)
