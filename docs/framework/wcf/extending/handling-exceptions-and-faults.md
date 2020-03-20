---
title: Zpracování výjimek a chyb
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: bca77b575be65513f9a792352e14e3f9bd7b4904
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185630"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="3e46b-102">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="3e46b-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="3e46b-103">Výjimky se používají ke komunikaci chyb místně v rámci služby nebo implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="3e46b-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="3e46b-104">Chyby, na druhé straně se používají ke komunikaci chyb přes hranice služby, například ze serveru klientovi nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="3e46b-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="3e46b-105">Kromě chyb dopravní kanály často používají mechanismy specifické pro přenos ke komunikaci chyb na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="3e46b-106">Například přenos HTTP používá stavové kódy, jako je například 404 ke komunikaci neexistující adresu URL koncového bodu (neexistuje žádný koncový bod pro odeslání chyby zpět).</span><span class="sxs-lookup"><span data-stu-id="3e46b-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="3e46b-107">Tento dokument se skládá ze tří částí, které poskytují pokyny pro vlastní autory kanálů.</span><span class="sxs-lookup"><span data-stu-id="3e46b-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="3e46b-108">První část obsahuje pokyny, kdy a jak definovat a vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="3e46b-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="3e46b-109">Druhá část obsahuje pokyny týkající se generování a spotřebovávání chyb.</span><span class="sxs-lookup"><span data-stu-id="3e46b-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="3e46b-110">Třetí část vysvětluje, jak poskytnout informace o trasování, které pomohou uživateli vlastního kanálu při odstraňování potíží se spuštěných aplikací.</span><span class="sxs-lookup"><span data-stu-id="3e46b-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="3e46b-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="3e46b-111">Exceptions</span></span>  
 <span data-ttu-id="3e46b-112">Existují dvě věci, které je třeba mít na paměti při vyvolání výjimky: Nejprve musí být typu, který umožňuje uživatelům psát správný kód, který může odpovídajícím způsobem reagovat na výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="3e46b-113">Za druhé, musí poskytnout dostatek informací pro uživatele pochopit, co se pokazilo, dopad selhání a jak to opravit.</span><span class="sxs-lookup"><span data-stu-id="3e46b-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="3e46b-114">V následujících částech jsou uvedeny pokyny týkající se typů výjimek a zpráv pro kanály WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="3e46b-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="3e46b-115">V dokumentu Pokyny pro návrh výjimek naleznete také obecné pokyny týkající se výjimek v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3e46b-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="3e46b-116">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="3e46b-116">Exception Types</span></span>  
 <span data-ttu-id="3e46b-117">Všechny výjimky vyváděné <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>kanály musí být <xref:System.ServiceModel.CommunicationException>buď <xref:System.TimeoutException?displayProperty=nameWithType>, nebo typ odvozený od .</span><span class="sxs-lookup"><span data-stu-id="3e46b-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="3e46b-118">(Výjimky, <xref:System.ObjectDisposedException> jako může být také vyvolána, ale pouze k označení, že volající kód zneužil kanál.</span><span class="sxs-lookup"><span data-stu-id="3e46b-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="3e46b-119">Pokud kanál se používá správně, musí vyvolat pouze dané výjimky.) WCF poskytuje sedm typů <xref:System.ServiceModel.CommunicationException> výjimek, které jsou odvozeny z a jsou určeny pro použití kanály.</span><span class="sxs-lookup"><span data-stu-id="3e46b-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="3e46b-120">Existují další <xref:System.ServiceModel.CommunicationException>odvozené výjimky, které jsou určeny pro použití jinými částmi systému.</span><span class="sxs-lookup"><span data-stu-id="3e46b-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="3e46b-121">Tyto typy výjimek jsou:</span><span class="sxs-lookup"><span data-stu-id="3e46b-121">These exception types are:</span></span>  
  
|<span data-ttu-id="3e46b-122">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="3e46b-122">Exception Type</span></span>|<span data-ttu-id="3e46b-123">Význam</span><span class="sxs-lookup"><span data-stu-id="3e46b-123">Meaning</span></span>|<span data-ttu-id="3e46b-124">Vnitřní obsah výjimky</span><span class="sxs-lookup"><span data-stu-id="3e46b-124">Inner Exception Content</span></span>|<span data-ttu-id="3e46b-125">Strategie obnovení</span><span class="sxs-lookup"><span data-stu-id="3e46b-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="3e46b-126">Adresa koncového bodu zadaná pro naslouchání je již používána.</span><span class="sxs-lookup"><span data-stu-id="3e46b-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="3e46b-127">Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="3e46b-128">Například.</span><span class="sxs-lookup"><span data-stu-id="3e46b-128">For example.</span></span> <span data-ttu-id="3e46b-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, <xref:System.Net.Sockets.SocketException>nebo .</span><span class="sxs-lookup"><span data-stu-id="3e46b-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="3e46b-130">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="3e46b-131">Proces není povolen přístup k adrese koncového bodu určené pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="3e46b-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="3e46b-132">Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="3e46b-133">Například <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>nebo .</span><span class="sxs-lookup"><span data-stu-id="3e46b-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="3e46b-134">Zkuste s různými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="3e46b-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="3e46b-135">Používaná <xref:System.ServiceModel.ICommunicationObject> položky jsou ve stavu Chybovaný (další informace naleznete v [tématu Principy změn stavu](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="3e46b-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="3e46b-136">Všimněte si, že když objekt s více čekající volání přechody do chybovaného stavu, pouze jedno volání <xref:System.ServiceModel.CommunicationObjectFaultedException>vyvolá výjimku, která souvisí s selhání a zbytek volání vyvolat .</span><span class="sxs-lookup"><span data-stu-id="3e46b-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="3e46b-137">Tato výjimka je obvykle vyvolána, protože aplikace přehlíží některé výjimky a pokusí se použít již vadný objekt, případně ve vlákně než ten, který zachytil původní výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="3e46b-138">Pokud je k dispozici poskytuje podrobnosti o vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="3e46b-139">Vytvořte nový objekt.</span><span class="sxs-lookup"><span data-stu-id="3e46b-139">Create a new object.</span></span> <span data-ttu-id="3e46b-140">Všimněte si, že <xref:System.ServiceModel.ICommunicationObject> v závislosti na tom, co způsobilo chybu na prvním místě, může být další práce potřebné k obnovení.</span><span class="sxs-lookup"><span data-stu-id="3e46b-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="3e46b-141">Používaná <xref:System.ServiceModel.ICommunicationObject> informace byla přerušena (další informace naleznete v [tématu Principy změn stavu](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="3e46b-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="3e46b-142">Podobně <xref:System.ServiceModel.CommunicationObjectFaultedException>jako , jeho výjimka <xref:System.ServiceModel.ICommunicationObject.Abort%2A> označuje, že aplikace volá objekt, případně z jiného vlákna, a objekt již není použitelný z tohoto důvodu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="3e46b-143">Pokud je k dispozici poskytuje podrobnosti o vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="3e46b-144">Vytvořte nový objekt.</span><span class="sxs-lookup"><span data-stu-id="3e46b-144">Create a new object.</span></span> <span data-ttu-id="3e46b-145">Všimněte si, že <xref:System.ServiceModel.ICommunicationObject> v závislosti na co způsobilo přerušení na prvním místě, může být další práce potřebné k obnovení.</span><span class="sxs-lookup"><span data-stu-id="3e46b-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="3e46b-146">Cílový vzdálený koncový bod nenaslouchá.</span><span class="sxs-lookup"><span data-stu-id="3e46b-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="3e46b-147">To může vyplývat z jakékoli části koncového bodu adresy je nesprávné, neřešitelné nebo koncový bod je dolů.</span><span class="sxs-lookup"><span data-stu-id="3e46b-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="3e46b-148">Příklady zahrnují chybu DNS, Správce front není k dispozici a služba není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="3e46b-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="3e46b-149">Vnitřní výjimka obsahuje podrobnosti, obvykle z podkladového přenosu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="3e46b-150">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-150">Try a different address.</span></span> <span data-ttu-id="3e46b-151">Odesílatel může také chvíli počkat a zkusit to znovu v případě, že služba neklesla.</span><span class="sxs-lookup"><span data-stu-id="3e46b-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="3e46b-152">Komunikační protokoly, jak je popsáno v zásadách koncového bodu, jsou neodpovídající mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="3e46b-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="3e46b-153">Například neshoda typu obsahu nebo maximální velikost zprávy byla překročena.</span><span class="sxs-lookup"><span data-stu-id="3e46b-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="3e46b-154">Pokud je k dispozici poskytuje další informace o konkrétní chybě protokolu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="3e46b-155">Například <xref:System.ServiceModel.QuotaExceededException> je vnitřní výjimka, když příčina chyby je vyšší MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="3e46b-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="3e46b-156">Obnovení: Ujistěte se, že odesílatel a přijaté nastavení protokolu odpovídají.</span><span class="sxs-lookup"><span data-stu-id="3e46b-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="3e46b-157">Jedním ze způsobů, jak to provést, je znovu importovat metadata (zásady) koncového bodu služby a použít vygenerovanou vazbu k opětovnému vytvoření kanálu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="3e46b-158">Vzdálený koncový bod naslouchá, ale není připraven ke zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e46b-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="3e46b-159">Pokud je k dispozici, vnitřní Exception poskytuje podrobnosti o chybě SOAP nebo na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="3e46b-160">Obnovení: Počkejte a opakujte operaci později.</span><span class="sxs-lookup"><span data-stu-id="3e46b-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="3e46b-161">Operaci se nepodařilo dokončit v časovém rámci.</span><span class="sxs-lookup"><span data-stu-id="3e46b-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="3e46b-162">Může poskytnout podrobnosti o časovém odnož.</span><span class="sxs-lookup"><span data-stu-id="3e46b-162">May provide details about the timeout.</span></span>|<span data-ttu-id="3e46b-163">Počkejte a opakujte operaci později.</span><span class="sxs-lookup"><span data-stu-id="3e46b-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="3e46b-164">Nový typ výjimky definujte pouze v případě, že tento typ odpovídá konkrétní strategii obnovení, která se liší od všech existujících typů výjimek.</span><span class="sxs-lookup"><span data-stu-id="3e46b-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="3e46b-165">Pokud definujete nový typ výjimky, <xref:System.ServiceModel.CommunicationException> musí být odvozen z nebo z jedné z jeho odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="3e46b-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="3e46b-166">Zprávy o výjimky</span><span class="sxs-lookup"><span data-stu-id="3e46b-166">Exception Messages</span></span>  
 <span data-ttu-id="3e46b-167">Zprávy o výjimce jsou zaměřeny na uživatele, nikoli na program, takže by měly poskytnout dostatečné informace, které uživateli pomohou pochopit a vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="3e46b-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="3e46b-168">Tři základní části zprávy o dobré výjimce jsou:</span><span class="sxs-lookup"><span data-stu-id="3e46b-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="3e46b-169">Co se stalo.</span><span class="sxs-lookup"><span data-stu-id="3e46b-169">What happened.</span></span> <span data-ttu-id="3e46b-170">Poskytněte jasný popis problému pomocí termínů, které se vztahují k uživatelskému prostředí.</span><span class="sxs-lookup"><span data-stu-id="3e46b-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="3e46b-171">Chybná zpráva o výjimce by například byla "Neplatná konfigurační část".</span><span class="sxs-lookup"><span data-stu-id="3e46b-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="3e46b-172">To ponechává uživateli přemýšlel, která část konfigurace je nesprávná a proč je nesprávná.</span><span class="sxs-lookup"><span data-stu-id="3e46b-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="3e46b-173">Vylepšená zpráva by "Neplatná konfigurační sekce \<customBinding>".</span><span class="sxs-lookup"><span data-stu-id="3e46b-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="3e46b-174">Ještě lepší zpráva by "Nelze přidat přenos s názvem myTransport do vazby s názvem myBinding, protože vazba již má přenos s názvem myTransport".</span><span class="sxs-lookup"><span data-stu-id="3e46b-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="3e46b-175">Jedná se o velmi specifickou zprávu pomocí termínů a názvů, které může uživatel snadno identifikovat v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e46b-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="3e46b-176">Stále však chybí několik klíčových součástí.</span><span class="sxs-lookup"><span data-stu-id="3e46b-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="3e46b-177">Význam chyby.</span><span class="sxs-lookup"><span data-stu-id="3e46b-177">The significance of the error.</span></span> <span data-ttu-id="3e46b-178">Pokud zpráva jasně neuvádí, co chyba znamená, uživatel se pravděpodobně bude ptát, zda se jedná o závažnou chybu nebo zda ji lze ignorovat.</span><span class="sxs-lookup"><span data-stu-id="3e46b-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="3e46b-179">Obecně zprávy by měly vést s významem nebo významem chyby.</span><span class="sxs-lookup"><span data-stu-id="3e46b-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="3e46b-180">Chcete-li zlepšit předchozí příklad, zpráva může být "ServiceHost se nepodařilo otevřít z důvodu chyby konfigurace: Nelze přidat přenos s názvem myTransport na vazbu s názvem myBinding, protože vazba již má přenos s názvem myTransport".</span><span class="sxs-lookup"><span data-stu-id="3e46b-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="3e46b-181">Jak by měl uživatel problém opravit.</span><span class="sxs-lookup"><span data-stu-id="3e46b-181">How the user should correct the problem.</span></span> <span data-ttu-id="3e46b-182">Nejdůležitější částí zprávy je pomoc uživateli vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="3e46b-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="3e46b-183">Zpráva by měla obsahovat některé pokyny nebo rady o tom, co zkontrolovat nebo opravit k vyřešení problému.</span><span class="sxs-lookup"><span data-stu-id="3e46b-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="3e46b-184">Například "ServiceHost se nepodařilo otevřít z důvodu chyby konfigurace: Nelze přidat přenos s názvem myTransport do vazby s názvem myBinding, protože vazba již má přenos s názvem myTransport.</span><span class="sxs-lookup"><span data-stu-id="3e46b-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="3e46b-185">Ujistěte se, že ve vazbě je pouze jedna přeprava".</span><span class="sxs-lookup"><span data-stu-id="3e46b-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="3e46b-186">Komunikace s chybami</span><span class="sxs-lookup"><span data-stu-id="3e46b-186">Communicating Faults</span></span>  
 <span data-ttu-id="3e46b-187">SOAP 1.1 a SOAP 1.2 oba definují specifickou strukturu pro chyby.</span><span class="sxs-lookup"><span data-stu-id="3e46b-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="3e46b-188">Existují určité rozdíly mezi dvěma specifikacemi, ale obecně Message a MessageFault typy se používají k vytvoření a využití chyb.</span><span class="sxs-lookup"><span data-stu-id="3e46b-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="3e46b-189">![Zpracování výjimek a závad](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2Porovnání chyb")</span><span class="sxs-lookup"><span data-stu-id="3e46b-189">![Handling exceptions and faults](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="3e46b-190">SOAP 1.2 Porucha (vlevo) a CHYBA SOAP 1.1 (vpravo).</span><span class="sxs-lookup"><span data-stu-id="3e46b-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="3e46b-191">Všimněte si, že v SOAP 1.1 pouze Fault element je obor názvů kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="3e46b-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="3e46b-192">SOAP definuje zprávu o chybě jako zprávu, která obsahuje pouze `<env:Fault>`prvek poruchy (prvek, jehož název je ) jako podřízený . `<env:Body>`</span><span class="sxs-lookup"><span data-stu-id="3e46b-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="3e46b-193">Obsah zlomového prvku se mírně liší mezi SOAP 1.1 a SOAP 1.2, jak je znázorněno na obrázku 1.</span><span class="sxs-lookup"><span data-stu-id="3e46b-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="3e46b-194">Třída však <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> normalizuje tyto rozdíly do jednoho objektového modelu:</span><span class="sxs-lookup"><span data-stu-id="3e46b-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```csharp
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 <span data-ttu-id="3e46b-195">Vlastnost `Code` odpovídá `env:Code` (nebo `faultCode` v SOAP 1.1) a identifikuje typ poruchy.</span><span class="sxs-lookup"><span data-stu-id="3e46b-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="3e46b-196">SOAP 1.2 definuje pět povolených hodnot pro `faultCode` (například Odesílatel a `Subcode` Příjemce) a definuje prvek, který může obsahovat libovolnou hodnotu podkódu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="3e46b-197">(Seznam povolených chybových kódů a jejich význam naleznete ve [specifikaci SOAP 1.2.)](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) SOAP 1.1 má mírně odlišný mechanismus: `faultCode` Definuje čtyři hodnoty (například Klient a Server), které lze rozšířit buď definováním zcela nových, `faultCodes`nebo pomocí notace tečky k vytvoření konkrétnější , například Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="3e46b-197">(See the [SOAP 1.2 specification](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="3e46b-198">Při použití MessageFault k programování chyb, FaultCode.Name a FaultCode.Namespace mapuje na název `env:Code` a obor názvů `faultCode`SOAP 1.2 nebo SOAP 1.1 .</span><span class="sxs-lookup"><span data-stu-id="3e46b-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="3e46b-199">FaultCode.SubCode mapuje `env:Subcode` pro SOAP 1.2 a je null pro SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="3e46b-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="3e46b-200">Pokud používáte soap 1.1, měli byste vytvořit nové dílčí kódy poruch (nebo nové chybové kódy), pokud je zajímavé programově rozlišit chybu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="3e46b-201">To je analogické k vytvoření nového typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="3e46b-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="3e46b-202">Měli byste se vyhnout použití tečky zápisu s SOAP 1.1 chybové kódy.</span><span class="sxs-lookup"><span data-stu-id="3e46b-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="3e46b-203">(Základní [profil WS-I](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) také odrazuje od použití zápisu tečky chybového kódu.)</span><span class="sxs-lookup"><span data-stu-id="3e46b-203">(The [WS-I Basic Profile](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) also discourages the use of the fault code dot notation.)</span></span>  
  
```csharp
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 <span data-ttu-id="3e46b-204">Vlastnost `Reason` odpovídá `env:Reason` (nebo `faultString` v SOAP 1.1) lidsky čitelný popis chybového stavu analogicky k zprávě výjimky.</span><span class="sxs-lookup"><span data-stu-id="3e46b-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="3e46b-205">Třída `FaultReason` (a `env:Reason/faultString`SOAP) má vestavěnou podporu pro více překladů v zájmu globalizace.</span><span class="sxs-lookup"><span data-stu-id="3e46b-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```csharp
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations
    {
       get;
    }  
  
 }  
```  
  
 <span data-ttu-id="3e46b-206">Obsah podrobností o chybě jsou vystaveny na `GetDetail` \<MessageFault `GetReaderAtDetailContents`pomocí různých metod, včetně T> a ().</span><span class="sxs-lookup"><span data-stu-id="3e46b-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="3e46b-207">Detail poruchy je neprůhledný prvek pro přenášení dalších podrobností o poruše.</span><span class="sxs-lookup"><span data-stu-id="3e46b-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="3e46b-208">To je užitečné, pokud existuje nějaký libovolný strukturovaný detail, který chcete provést s chybou.</span><span class="sxs-lookup"><span data-stu-id="3e46b-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="3e46b-209">Generování chyb</span><span class="sxs-lookup"><span data-stu-id="3e46b-209">Generating Faults</span></span>  
 <span data-ttu-id="3e46b-210">Tato část vysvětluje proces generování chyby v reakci na chybový stav zjištěný v kanálu nebo ve vlastnosti zprávy vytvořené kanálem.</span><span class="sxs-lookup"><span data-stu-id="3e46b-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="3e46b-211">Typickým příkladem je odeslání chyby v odpovědi na zprávu požadavku, která obsahuje neplatná data.</span><span class="sxs-lookup"><span data-stu-id="3e46b-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="3e46b-212">Při generování chyby by vlastní kanál neměl odesílat chybu přímo, spíše by měl vyvolat výjimku a nechat výše uvedenou vrstvu rozhodnout, zda převést tuto výjimku na chybu a jak ji odeslat.</span><span class="sxs-lookup"><span data-stu-id="3e46b-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="3e46b-213">Chcete-li pomoci v tomto převodu, kanál by měl poskytnout `FaultConverter` implementaci, která může převést výjimku vyváděnou vlastní kanál na příslušnou chybu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="3e46b-214">`FaultConverter`je definována jako:</span><span class="sxs-lookup"><span data-stu-id="3e46b-214">`FaultConverter` is defined as:</span></span>  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
}  
```  
  
 <span data-ttu-id="3e46b-215">Každý kanál, který generuje vlastní `FaultConverter` chyby, musí `GetProperty<FaultConverter>`implementovat a vrátit z volání do .</span><span class="sxs-lookup"><span data-stu-id="3e46b-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="3e46b-216">Vlastní `OnTryCreateFaultMessage` implementace musí buď převést výjimku na chybu nebo `FaultConverter`delegovat na vnitřní kanál .</span><span class="sxs-lookup"><span data-stu-id="3e46b-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="3e46b-217">Pokud kanál je přenos musí převést výjimku nebo delegovat `FaultConverter` na `FaultConverter` kodéru nebo výchozí k dispozici v WCF .</span><span class="sxs-lookup"><span data-stu-id="3e46b-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="3e46b-218">Výchozí `FaultConverter` převede chyby odpovídající chybové zprávy určené WS-Adresování a SOAP.</span><span class="sxs-lookup"><span data-stu-id="3e46b-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="3e46b-219">Zde je `OnTryCreateFaultMessage` příklad implementace.</span><span class="sxs-lookup"><span data-stu-id="3e46b-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```csharp
public override bool OnTryCreateFaultMessage(Exception exception,
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,
                   out message);  
#else  
    FaultConverter inner =
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="3e46b-220">Důsledkem tohoto vzoru je, že výjimky vyzvané mezi vrstvami pro chybové stavy, které vyžadují chyby, musí obsahovat dostatek informací pro odpovídající generátor chyb k vytvoření správné chyby.</span><span class="sxs-lookup"><span data-stu-id="3e46b-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="3e46b-221">Jako vlastní autor kanálu můžete definovat typy výjimek, které odpovídají různým poruchovým podmínkám, pokud takové výjimky ještě neexistují.</span><span class="sxs-lookup"><span data-stu-id="3e46b-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="3e46b-222">Všimněte si, že výjimky procházející vrstvy kanálu by měly komunikovat chybový stav spíše než neprůhledná data poruchy.</span><span class="sxs-lookup"><span data-stu-id="3e46b-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="3e46b-223">Kategorie poruch</span><span class="sxs-lookup"><span data-stu-id="3e46b-223">Fault Categories</span></span>  
 <span data-ttu-id="3e46b-224">Obecně existují tři kategorie závad:</span><span class="sxs-lookup"><span data-stu-id="3e46b-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="3e46b-225">Chyby, které jsou všudypřítomné v celém zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="3e46b-226">Tyto chyby může dojít v libovolné vrstvě v zásobníku kanálu, například InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="3e46b-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="3e46b-227">Chyby, které lze narazit kdekoli nad určitou vrstvu v zásobníku například některé chyby, které se týkající se toku transakce nebo role zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e46b-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="3e46b-228">Chyby, které jsou směrovány na jednu vrstvu v zásobníku, například chyby, jako jsou chyby pořadového čísla WS-RM.</span><span class="sxs-lookup"><span data-stu-id="3e46b-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="3e46b-229">Kategorie 1.</span><span class="sxs-lookup"><span data-stu-id="3e46b-229">Category 1.</span></span> <span data-ttu-id="3e46b-230">Chyby jsou obecně WS adresování a SOAP chyby.</span><span class="sxs-lookup"><span data-stu-id="3e46b-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="3e46b-231">Základní `FaultConverter` třída poskytovaná WCF převádí chyby odpovídající chybové zprávy určené WS-Adresování a SOAP, takže není třeba zpracovat převod těchto výjimek sami.</span><span class="sxs-lookup"><span data-stu-id="3e46b-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="3e46b-232">Kategorie 2.</span><span class="sxs-lookup"><span data-stu-id="3e46b-232">Category 2.</span></span> <span data-ttu-id="3e46b-233">Chyby dojít, když vrstva přidá vlastnost zprávy, která není zcela využívat informace o zprávě, která se týká této vrstvy.</span><span class="sxs-lookup"><span data-stu-id="3e46b-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="3e46b-234">Chyby mohou být zjištěny později, když vyšší vrstva požádá vlastnost zprávy o další zpracování informací o zprávě.</span><span class="sxs-lookup"><span data-stu-id="3e46b-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="3e46b-235">Tyto kanály `GetProperty` by měly implementovat zadané dříve povolit vyšší vrstvy odeslat zpět správnou chybu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="3e46b-236">Příkladem je TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="3e46b-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="3e46b-237">Tato vlastnost je přidána do zprávy bez úplného ověření všech dat v záhlaví (to může zahrnovat kontaktování koordinátora distribuovaných transakcí (DTC).</span><span class="sxs-lookup"><span data-stu-id="3e46b-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="3e46b-238">Kategorie 3.</span><span class="sxs-lookup"><span data-stu-id="3e46b-238">Category 3.</span></span> <span data-ttu-id="3e46b-239">Chyby jsou generovány a odesílány pouze jednou vrstvou v procesoru.</span><span class="sxs-lookup"><span data-stu-id="3e46b-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="3e46b-240">Proto jsou všechny výjimky obsaženy ve vrstvě.</span><span class="sxs-lookup"><span data-stu-id="3e46b-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="3e46b-241">Chcete-li zlepšit konzistenci mezi kanály a usnadnit údržbu, vlastní kanál by měl použít vzor zadaný dříve generovat chybové zprávy i pro vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="3e46b-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="3e46b-242">Interpretace přijatých chyb</span><span class="sxs-lookup"><span data-stu-id="3e46b-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="3e46b-243">Tato část obsahuje pokyny pro generování příslušné výjimky při přijímání chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="3e46b-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="3e46b-244">Rozhodovací strom pro zpracování zprávy v každé vrstvě v zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="3e46b-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="3e46b-245">Pokud vrstva považuje zprávu za neplatnou, měla by provést zpracování "neplatné zprávy".</span><span class="sxs-lookup"><span data-stu-id="3e46b-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="3e46b-246">Takové zpracování je specifické pro vrstvu, ale může zahrnovat uvolnění zprávy, trasování nebo vyvolání výjimky, která získá převedena na chybu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="3e46b-247">Mezi příklady patří zabezpečení přijímající zprávu, která není správně zabezpečena, nebo rm přijímající zprávu se špatným pořadovým číslem.</span><span class="sxs-lookup"><span data-stu-id="3e46b-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="3e46b-248">V opačném případě pokud zpráva je zpráva, která se vztahuje konkrétně na vrstvu a zpráva není smysluplné mimo interakci vrstvy, vrstva by měla zpracovat chybový stav.</span><span class="sxs-lookup"><span data-stu-id="3e46b-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="3e46b-249">Příkladem je chyba ODMÍTNUTÁ RM, která nemá smysl pro vrstvy nad kanálem RM a znamená chybovat kanál RM a vyvolávat z čekajících operací.</span><span class="sxs-lookup"><span data-stu-id="3e46b-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="3e46b-250">V opačném případě by měla být vrácena zpráva z Request() nebo Receive().</span><span class="sxs-lookup"><span data-stu-id="3e46b-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="3e46b-251">To zahrnuje případy, kdy vrstva rozpozná chybu, ale chyba pouze označuje, že požadavek se nezdařil a neznamená chybování kanálu a vyvolání z čekajících operací.</span><span class="sxs-lookup"><span data-stu-id="3e46b-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="3e46b-252">Chcete-li zlepšit použitelnost v takovém případě `GetProperty<FaultConverter>` by `FaultConverter` měla vrstva implementovat a vrátit odvozenou `OnTryCreateException`třídu, která může převést chybu na výjimku přepsáním .</span><span class="sxs-lookup"><span data-stu-id="3e46b-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="3e46b-253">Následující objektový model podporuje převod zpráv na výjimky:</span><span class="sxs-lookup"><span data-stu-id="3e46b-253">The following object model supports converting messages to exceptions:</span></span>  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
}  
```  
  
 <span data-ttu-id="3e46b-254">Vrstva kanálu `GetProperty<FaultConverter>` můžete implementovat pro podporu převodu chybové zprávy na výjimky.</span><span class="sxs-lookup"><span data-stu-id="3e46b-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="3e46b-255">Chcete-li tak `OnTryCreateException` učinit, přepsat a zkontrolujte zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="3e46b-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="3e46b-256">Pokud je rozpoznán, proveďte převod, jinak požádejte vnitřní kanál, aby jej převedl.</span><span class="sxs-lookup"><span data-stu-id="3e46b-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="3e46b-257">Kanály přenosu `FaultConverter.GetDefaultFaultConverter` by měldelegovat získat výchozí SOAP/WS adresování FaultConverter.</span><span class="sxs-lookup"><span data-stu-id="3e46b-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="3e46b-258">Typická implementace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3e46b-258">A typical implementation looks like this:</span></span>  
  
```csharp
public override bool OnTryCreateException(  
                            Message message,
                            MessageFault fault,
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="3e46b-259">Pro konkrétní chybové podmínky, které mají odlišné scénáře `ProtocolException`obnovení, zvažte definování odvozené třídy .</span><span class="sxs-lookup"><span data-stu-id="3e46b-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="3e46b-260">Zpracování musí pochopit</span><span class="sxs-lookup"><span data-stu-id="3e46b-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="3e46b-261">SOAP definuje obecnou chybu pro signalizaci, že příjemce nepochopil požadovanou hlavičku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="3e46b-262">Tato chyba se `mustUnderstand` označuje jako chyba.</span><span class="sxs-lookup"><span data-stu-id="3e46b-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="3e46b-263">V WCF vlastní kanály nikdy generovat `mustUnderstand` chyby.</span><span class="sxs-lookup"><span data-stu-id="3e46b-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="3e46b-264">Místo toho WCF Dispatcher, který je umístěn v horní části zásobníku komunikace WCF, zkontroluje, zda všechny hlavičky, které byly označeny jako MustUnderstand =true byly pochopeny základní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="3e46b-265">Pokud některé nebyly pochopeny, `mustUnderstand` chyba je generována v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="3e46b-266">(Uživatel se může rozhodnout `mustUnderstand` toto zpracování vypnout a aplikaci přijímat všechna záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e46b-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="3e46b-267">V takovém případě je aplikace `mustUnderstand` zodpovědná za zpracování.) Vygenerovaná chyba obsahuje hlavičku NotUnderstood, která obsahuje názvy všech záhlaví s MustUnderstand=true, které nebyly pochopeny.</span><span class="sxs-lookup"><span data-stu-id="3e46b-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="3e46b-268">Pokud váš kanál protokolu odešle vlastní záhlaví s `mustUnderstand` MustUnderstand=true a obdrží chybu, musí zjistit, zda je tato chyba způsobena hlavičkou, kterou odeslal.</span><span class="sxs-lookup"><span data-stu-id="3e46b-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="3e46b-269">Ve `MessageFault` třídě jsou dva členy, které jsou užitečné pro toto:</span><span class="sxs-lookup"><span data-stu-id="3e46b-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="3e46b-270">`IsMustUnderstandFault`pokud `true` se závada `mustUnderstand` nachází v závadě.</span><span class="sxs-lookup"><span data-stu-id="3e46b-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="3e46b-271">`WasHeaderNotUnderstood`vrátí, `true` pokud je záhlaví se zadaným názvem a oborem názvů zahrnuto do chyby jako hlavička NotUnderstood.</span><span class="sxs-lookup"><span data-stu-id="3e46b-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="3e46b-272">V opačném `false`případě vrátí .</span><span class="sxs-lookup"><span data-stu-id="3e46b-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="3e46b-273">Pokud kanál vyzařuje záhlaví, které je označeno MustUnderstand = true, pak by tato `mustUnderstand` vrstva měla také implementovat vzor rozhraní API pro generování výjimek a měla by převést chyby způsobené tímto záhlavím na užitečnější výjimku, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="3e46b-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="3e46b-274">Trasování</span><span class="sxs-lookup"><span data-stu-id="3e46b-274">Tracing</span></span>  
 <span data-ttu-id="3e46b-275">Rozhraní .NET Framework poskytuje mechanismus pro sledování spuštění programu jako způsob, jak pomoci diagnostikovat produkční aplikace nebo občasné problémy, kde není možné pouze připojit ladicí program a krokovat kód.</span><span class="sxs-lookup"><span data-stu-id="3e46b-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="3e46b-276">Základní součásti tohoto mechanismu jsou <xref:System.Diagnostics?displayProperty=nameWithType> v oboru názvů a skládají se z:</span><span class="sxs-lookup"><span data-stu-id="3e46b-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="3e46b-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj trasovací informace, které mají být zapsány , <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, což je abstraktní <xref:System.Diagnostics.TraceSource> základní třída pro konkrétní posluchače, které přijímají informace, které mají být vysledovány z a výstup do cíle specifické pro posluchače.</span><span class="sxs-lookup"><span data-stu-id="3e46b-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="3e46b-278">Například <xref:System.Diagnostics.XmlWriterTraceListener> výstupy trasování informace do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="3e46b-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="3e46b-279">Nakonec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, který umožňuje uživateli aplikace řídit podrobnosti o trasování a je obvykle zadán v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="3e46b-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="3e46b-280">Kromě základních součástí můžete k zobrazení a prohledání trasování WCF použít [nástroj prohlížeč trasování služby (SvcTraceViewer.exe).](../service-trace-viewer-tool-svctraceviewer-exe.md)</span><span class="sxs-lookup"><span data-stu-id="3e46b-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="3e46b-281">Nástroj je navržen speciálně pro trasovací soubory generované <xref:System.Diagnostics.XmlWriterTraceListener>WCF a psaný pomocí .</span><span class="sxs-lookup"><span data-stu-id="3e46b-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="3e46b-282">Následující obrázek znázorňuje různé součásti, které se podílejí na trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="3e46b-283">![Zpracování výjimek a závad](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="3e46b-283">![Handling exceptions and faults](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="3e46b-284">Trasování z vlastního kanálu</span><span class="sxs-lookup"><span data-stu-id="3e46b-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="3e46b-285">Vlastní kanály by měly zapisovat trasovací zprávy, které by pomohly při diagnostice problémů, když není možné připojit ladicí program ke spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3e46b-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="3e46b-286">To zahrnuje dva úkoly na vysoké <xref:System.Diagnostics.TraceSource> úrovni: Vytváření instancí a volání jeho metody pro zápis trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="3e46b-287">Při vytváření instancí <xref:System.Diagnostics.TraceSource>a se zadaný řetězec stane názvem tohoto zdroje.</span><span class="sxs-lookup"><span data-stu-id="3e46b-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="3e46b-288">Tento název se používá ke konfiguraci (povolit/zakázat/nastavit úroveň trasování) zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="3e46b-289">Zobrazí se také v samotném výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="3e46b-290">Vlastní kanály by měly používat jedinečný zdrojový název, který čtenářům výstupu trasování pomůže pochopit, odkud pocházejí informace o trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="3e46b-291">Použití názvu sestavení, které zapisuje informace jako název zdroje trasování je běžnou praxí.</span><span class="sxs-lookup"><span data-stu-id="3e46b-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="3e46b-292">Například WCF používá System.ServiceModel jako zdroj trasování pro informace napsané ze sestavení System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="3e46b-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="3e46b-293">Jakmile máte zdroj trasování, <xref:System.Diagnostics.TraceSource.TraceData%2A>zavoláte jeho , <xref:System.Diagnostics.TraceSource.TraceEvent%2A>nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metody pro zápis trasovacích položek do posluchačů trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="3e46b-294">Pro každou položku trasování, kterou zapíšete, je třeba klasifikovat typ události jako jeden z typů událostí definovaných v . <xref:System.Diagnostics.TraceEventType></span><span class="sxs-lookup"><span data-stu-id="3e46b-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="3e46b-295">Tato klasifikace a nastavení úrovně trasování v konfiguraci určují, zda je položka trasování výstupem na schytavku.</span><span class="sxs-lookup"><span data-stu-id="3e46b-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="3e46b-296">Například nastavení úrovně trasování `Warning` v `Warning` `Error` konfiguraci umožňuje a `Critical` trasování položky, které mají být zapsány, ale blokuje informace a podrobné položky.</span><span class="sxs-lookup"><span data-stu-id="3e46b-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="3e46b-297">Zde je příklad vytvoření instance zdroje trasování a zápisu položky na úrovni informace:</span><span class="sxs-lookup"><span data-stu-id="3e46b-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="3e46b-298">Důrazně doporučujeme zadat název zdroje trasování, který je jedinečný pro váš vlastní kanál, který pomůže sledovat výstupní čtečky pochopit, odkud výstup pochází.</span><span class="sxs-lookup"><span data-stu-id="3e46b-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="3e46b-299">Integrace s prohlížečem trasování</span><span class="sxs-lookup"><span data-stu-id="3e46b-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="3e46b-300">Trasování generované kanálem může být výstup ve formátu čitelné [masce služby (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pomocí <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="3e46b-301">To není něco, co musíte jako vývojář kanálu udělat.</span><span class="sxs-lookup"><span data-stu-id="3e46b-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="3e46b-302">Spíše je uživatel aplikace (nebo osoba řešení potíží s aplikací), který potřebuje nakonfigurovat tento naslouchací proces trasování v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e46b-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="3e46b-303">Například následující konfigurace výstupy trasování <xref:System.ServiceModel?displayProperty=nameWithType> `Microsoft.Samples.Udp` informace z `TraceEventsFile.e2e`obou a do souboru s názvem :</span><span class="sxs-lookup"><span data-stu-id="3e46b-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="3e46b-304">Trasování strukturovaných dat</span><span class="sxs-lookup"><span data-stu-id="3e46b-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="3e46b-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>má <xref:System.Diagnostics.TraceSource.TraceData%2A> metodu, která trvá jeden nebo více objektů, které mají být zahrnuty do položky trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="3e46b-306">Obecně platí, <xref:System.Object.ToString%2A?displayProperty=nameWithType> že metoda je volána na každý objekt a výsledný řetězec je zapsán jako součást položky trasování.</span><span class="sxs-lookup"><span data-stu-id="3e46b-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="3e46b-307">Při <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> použití k výstupu trasování, <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> můžete předat <xref:System.Diagnostics.TraceSource.TraceData%2A>jako datový objekt .</span><span class="sxs-lookup"><span data-stu-id="3e46b-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="3e46b-308">Výsledná položka trasování zahrnuje xml <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>poskytované .</span><span class="sxs-lookup"><span data-stu-id="3e46b-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e46b-309">Zde je ukázková položka s daty aplikace XML:</span><span class="sxs-lookup"><span data-stu-id="3e46b-309">Here is an example entry with XML application data:</span></span>  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 <span data-ttu-id="3e46b-310">Prohlížeč trasování WCF rozumí schématu `TraceRecord` dříve zobrazeného prvku a extrahuje data z podřízených prvků a zobrazí je v tabulkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="3e46b-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="3e46b-311">Váš kanál by měl používat toto schéma při trasování strukturovaných dat aplikace pomoci Uživatelům Svctraceviewer.exe číst data.</span><span class="sxs-lookup"><span data-stu-id="3e46b-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
