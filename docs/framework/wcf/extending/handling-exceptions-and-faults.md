---
title: "Zpracování výjimek a chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf621ce53b1e0aa5fd95adbd9de01bdbd97392bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="705ac-102">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="705ac-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="705ac-103">Výjimky se používají ke komunikaci chyby místně v rámci služby nebo implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="705ac-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="705ac-104">Chyb, na druhé straně, se použijí ke komunikaci chyby napříč hranicemi služby, například ze serveru do klienta a naopak.</span><span class="sxs-lookup"><span data-stu-id="705ac-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="705ac-105">Kromě chyb používají přenosové kanály mechanismy specifické pro přenos často ke komunikaci chyb na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="705ac-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="705ac-106">Například přenos HTTP používá stavové kódy, jako je například 404 ke komunikaci neexistující adresu URL koncového bodu (neexistuje žádný koncový bod, který má být zaslán zpět chybu).</span><span class="sxs-lookup"><span data-stu-id="705ac-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="705ac-107">Tento dokument se skládá ze tří oddílů, které poskytují pokyny k vlastním kanálu autoři.</span><span class="sxs-lookup"><span data-stu-id="705ac-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="705ac-108">První část obsahuje pokyny k kdy a jak definovat a generování výjimek.</span><span class="sxs-lookup"><span data-stu-id="705ac-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="705ac-109">Druhá část obsahuje pokyny ohledně generování a využívání chyb.</span><span class="sxs-lookup"><span data-stu-id="705ac-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="705ac-110">Třetí část vysvětluje, jak poskytnout informace o trasování a řešení potíží s běžící aplikací usnadňuje uživateli vlastní kanál.</span><span class="sxs-lookup"><span data-stu-id="705ac-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="705ac-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="705ac-111">Exceptions</span></span>  
 <span data-ttu-id="705ac-112">Mějte na paměti při vyvolání k výjimce dvě věci: nejprve musí být typu, který umožňuje uživatelům správně napsat správný kód, který může reagovat na výjimku.</span><span class="sxs-lookup"><span data-stu-id="705ac-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="705ac-113">Druhý je poskytnout dostatek informací pro porozumět, co došlo k chybě, dopad selhání a jeho řešení.</span><span class="sxs-lookup"><span data-stu-id="705ac-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="705ac-114">Následující části poskytují pokyny ohledně typy výjimek a zprávy pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanály.</span><span class="sxs-lookup"><span data-stu-id="705ac-114">The following sections give guidance around exception types and messages for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channels.</span></span> <span data-ttu-id="705ac-115">Je také obecné pokyny ohledně výjimky v rozhraní .NET obecných zásad návrhu pro dokument výjimky.</span><span class="sxs-lookup"><span data-stu-id="705ac-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="705ac-116">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="705ac-116">Exception Types</span></span>  
 <span data-ttu-id="705ac-117">Všechny výjimky vyvolané kanály musí být buď <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, nebo z odvozený typ. <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="705ac-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="705ac-118">(Výjimky jako <xref:System.ObjectDisposedException> může být rovněž vyvolána, ale pouze pro označení volající kód má došlo ke zneužití kanál.</span><span class="sxs-lookup"><span data-stu-id="705ac-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="705ac-119">Pokud se používá kanál, se musí pouze throw dané výjimky.) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje sedm typy výjimek, které jsou odvozeny od <xref:System.ServiceModel.CommunicationException> a jsou určeny k použití podle kanály.</span><span class="sxs-lookup"><span data-stu-id="705ac-119">If a channel is used correctly, it must only throw the given exceptions.) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="705ac-120">Existují jiné <xref:System.ServiceModel.CommunicationException>-odvozené výjimky, které jsou určeny k použití podle dalších částí systému.</span><span class="sxs-lookup"><span data-stu-id="705ac-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="705ac-121">Tyto typy výjimek jsou:</span><span class="sxs-lookup"><span data-stu-id="705ac-121">These exception types are:</span></span>  
  
|<span data-ttu-id="705ac-122">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="705ac-122">Exception Type</span></span>|<span data-ttu-id="705ac-123">Význam</span><span class="sxs-lookup"><span data-stu-id="705ac-123">Meaning</span></span>|<span data-ttu-id="705ac-124">Vnitřní výjimka obsahu</span><span class="sxs-lookup"><span data-stu-id="705ac-124">Inner Exception Content</span></span>|<span data-ttu-id="705ac-125">Strategie obnovení</span><span class="sxs-lookup"><span data-stu-id="705ac-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="705ac-126">Zadaná adresa koncového bodu pro naslouchání se už používá.</span><span class="sxs-lookup"><span data-stu-id="705ac-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="705ac-127">Pokud existuje, obsahuje další podrobnosti o této chybě přenosu, který způsobil výjimku.</span><span class="sxs-lookup"><span data-stu-id="705ac-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="705ac-128">Například.</span><span class="sxs-lookup"><span data-stu-id="705ac-128">For example.</span></span> <span data-ttu-id="705ac-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, nebo <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="705ac-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="705ac-130">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="705ac-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="705ac-131">Proces není povolen přístup k zadaná adresa koncového bodu pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="705ac-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="705ac-132">Pokud existuje, obsahuje další podrobnosti o této chybě přenosu, který způsobil výjimku.</span><span class="sxs-lookup"><span data-stu-id="705ac-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="705ac-133">Například <xref:System.IO.PipeException>, nebo <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="705ac-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="705ac-134">Opakujte s jinými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="705ac-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="705ac-135"><xref:System.ServiceModel.ICommunicationObject> Používá je v chybném stavu (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="705ac-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="705ac-136">Všimněte si, že při aktualizaci objektu s více čekající na vyřízení přechody volání chybném stavu pouze jedno volání vyvolá výjimku, která souvisí s chybou a zbytek throw volání <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="705ac-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="705ac-137">Tato výjimka je obvykle vyvolána, protože aplikace overlooks některé výjimky a pokusí se použít objekt již chybný, pravděpodobně na vlákno než ten, který vyvolal výjimku původní.</span><span class="sxs-lookup"><span data-stu-id="705ac-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="705ac-138">Pokud je k dispozici poskytuje podrobnosti o informacích o vnitřní výjimce.</span><span class="sxs-lookup"><span data-stu-id="705ac-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="705ac-139">Vytvořte nový objekt.</span><span class="sxs-lookup"><span data-stu-id="705ac-139">Create a new object.</span></span> <span data-ttu-id="705ac-140">Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> k poruch na prvním místě, může být jiné práce potřebné k obnovení.</span><span class="sxs-lookup"><span data-stu-id="705ac-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="705ac-141"><xref:System.ServiceModel.ICommunicationObject> Používá byla přerušena (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="705ac-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="705ac-142">Podobně jako <xref:System.ServiceModel.CommunicationObjectFaultedException>, jeho výjimka označuje aplikace volal <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na objekt, případně z jiného vlákna, a objekt již není použitelné z tohoto důvodu.</span><span class="sxs-lookup"><span data-stu-id="705ac-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="705ac-143">Pokud je k dispozici poskytuje podrobnosti o informacích o vnitřní výjimce.</span><span class="sxs-lookup"><span data-stu-id="705ac-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="705ac-144">Vytvořte nový objekt.</span><span class="sxs-lookup"><span data-stu-id="705ac-144">Create a new object.</span></span> <span data-ttu-id="705ac-145">Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> k přerušení na prvním místě, může být jiné práce potřebné k obnovení.</span><span class="sxs-lookup"><span data-stu-id="705ac-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="705ac-146">Vzdálený koncový bod cílové nenaslouchá.</span><span class="sxs-lookup"><span data-stu-id="705ac-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="705ac-147">Může to být důsledkem libovolná součást adresa koncového bodu je nesprávná, irresolvable nebo koncový bod se dolů.</span><span class="sxs-lookup"><span data-stu-id="705ac-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="705ac-148">Mezi příklady patří chyby DNS, správce front není k dispozici a služba není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="705ac-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="705ac-149">V popisu vnitřní výjimky poskytuje podrobnosti, obvykle ze základní přenos.</span><span class="sxs-lookup"><span data-stu-id="705ac-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="705ac-150">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="705ac-150">Try a different address.</span></span> <span data-ttu-id="705ac-151">Alternativně může odesílatel chvíli počkejte a zkuste to znovu, v případě, že byla služba dolů</span><span class="sxs-lookup"><span data-stu-id="705ac-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="705ac-152">Komunikační protokoly, jak je popsáno pomocí zásad pro koncový bod, se neshoda mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="705ac-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="705ac-153">Například počet rámců Neshoda typu obsahu nebo zprávy maximální velikost překročena.</span><span class="sxs-lookup"><span data-stu-id="705ac-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="705ac-154">Pokud je k dispozici poskytuje další informace o chybě určitý protokol.</span><span class="sxs-lookup"><span data-stu-id="705ac-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="705ac-155">Například <xref:System.ServiceModel.QuotaExceededException> při příčina chyby je vyšší než MaxReceivedMessageSize je v popisu vnitřní výjimky.</span><span class="sxs-lookup"><span data-stu-id="705ac-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="705ac-156">Obnovení: Zkontrolujte odesílatele a přijaté protokolu, které odpovídají nastavení.</span><span class="sxs-lookup"><span data-stu-id="705ac-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="705ac-157">Jedním ze způsobů k tomu je znovu importovat metadata koncový bod služby (zásady) a znovu vytvořit kanál pomocí generovaného vazby.</span><span class="sxs-lookup"><span data-stu-id="705ac-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="705ac-158">Vzdálený koncový bod naslouchá, ale není připravený ke zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="705ac-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="705ac-159">Pokud je k dispozici, v popisu vnitřní výjimky poskytuje chybu protokolu SOAP nebo podrobnosti o chybě transportní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="705ac-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="705ac-160">Obnovení: Počkejte a opakujte operaci později.</span><span class="sxs-lookup"><span data-stu-id="705ac-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="705ac-161">Operaci se nepodařilo dokončit během časového limitu.</span><span class="sxs-lookup"><span data-stu-id="705ac-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="705ac-162">Poskytnout informace o časový limit.</span><span class="sxs-lookup"><span data-stu-id="705ac-162">May provide details about the timeout.</span></span>|<span data-ttu-id="705ac-163">Počkejte a opakujte operaci později.</span><span class="sxs-lookup"><span data-stu-id="705ac-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="705ac-164">Definujte nový typ výjimky, pouze v případě, že tento typ odpovídá konkrétní obnovení strategie, který se liší od všechny existující typy výjimek.</span><span class="sxs-lookup"><span data-stu-id="705ac-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="705ac-165">Pokud definujete nový typ výjimky, musí být odvozeny od <xref:System.ServiceModel.CommunicationException> nebo jeden z jejich odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="705ac-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="705ac-166">Zprávy o výjimkách</span><span class="sxs-lookup"><span data-stu-id="705ac-166">Exception Messages</span></span>  
 <span data-ttu-id="705ac-167">Zprávy o výjimkách jsou zaměřeny na uživatele není program, se musí poskytovat dostatečné informace pomoct pochopit a vyřešit problém s uživateli.</span><span class="sxs-lookup"><span data-stu-id="705ac-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="705ac-168">Jsou tři základní části zpráva dobrý výjimky:</span><span class="sxs-lookup"><span data-stu-id="705ac-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="705ac-169">Co se přihodilo.</span><span class="sxs-lookup"><span data-stu-id="705ac-169">What happened.</span></span> <span data-ttu-id="705ac-170">Zadejte výstižný popis problému pomocí termínů, které se vztahují k možnosti pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="705ac-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="705ac-171">Například by zpráva chybná výjimky "Neplatný konfigurační oddíl".</span><span class="sxs-lookup"><span data-stu-id="705ac-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="705ac-172">Zůstane uživatele vás zajímá, které konfigurační oddíl jsou nesprávné a proč je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="705ac-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="705ac-173">Vylepšené zprávy by "Neplatný konfigurační oddíl \<customBinding >".</span><span class="sxs-lookup"><span data-stu-id="705ac-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="705ac-174">By být ještě lepší zpráva "nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenos s názvem myTransport".</span><span class="sxs-lookup"><span data-stu-id="705ac-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="705ac-175">Toto je velmi konkrétní zprávu pomocí podmínek a názvy, které může uživatel snadno identifikovat v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="705ac-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="705ac-176">Existují však stále několik klíčové komponenty chybí.</span><span class="sxs-lookup"><span data-stu-id="705ac-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="705ac-177">Násobek chyba.</span><span class="sxs-lookup"><span data-stu-id="705ac-177">The significance of the error.</span></span> <span data-ttu-id="705ac-178">Pokud zpráva jasně neurčí, co znamená chybu, uživatel bude pravděpodobně zajímat, zda se jedná o závažné chybě nebo pokud můžete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="705ac-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="705ac-179">Obecně platí by měla vést zprávy s význam nebo násobek chyby.</span><span class="sxs-lookup"><span data-stu-id="705ac-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="705ac-180">Ke zlepšení předchozí příklad, může být zpráva "hostitel služby se nezdařilo otevřít z důvodu chyby konfigurace: nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenos s názvem myTransport".</span><span class="sxs-lookup"><span data-stu-id="705ac-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="705ac-181">Jak uživatel by měl problém opravit.</span><span class="sxs-lookup"><span data-stu-id="705ac-181">How the user should correct the problem.</span></span> <span data-ttu-id="705ac-182">Nejdůležitější část zprávy pomáhá uživatele opravu problému.</span><span class="sxs-lookup"><span data-stu-id="705ac-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="705ac-183">Zpráva by měla obsahovat některé pokyny nebo pomocné parametry o tom, jak zkontrolovat nebo opravte problém odstraněn.</span><span class="sxs-lookup"><span data-stu-id="705ac-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="705ac-184">Například "hostitel služby se nezdařilo otevřít z důvodu chyby konfigurace: nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenos s názvem myTransport.</span><span class="sxs-lookup"><span data-stu-id="705ac-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="705ac-185">Ujistěte se, že je vazba pouze jeden přenos".</span><span class="sxs-lookup"><span data-stu-id="705ac-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="705ac-186">Komunikaci chyb</span><span class="sxs-lookup"><span data-stu-id="705ac-186">Communicating Faults</span></span>  
 <span data-ttu-id="705ac-187">SOAP 1.1 a SOAP 1.2 definovat konkrétní strukturu pro chyb.</span><span class="sxs-lookup"><span data-stu-id="705ac-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="705ac-188">Existují určité rozdíly mezi dvěma specifikace, ale obecně platí, zprávu a MessageFault typy slouží k vytvoření a využívat chyb.</span><span class="sxs-lookup"><span data-stu-id="705ac-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="705ac-189">![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1. 1AndSOAP1 2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="705ac-189">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="705ac-190">SOAP 1.2 selhání (vlevo) a chybu protokolu SOAP 1.1 (vpravo).</span><span class="sxs-lookup"><span data-stu-id="705ac-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="705ac-191">Všimněte si, že v protokolu SOAP 1.1 pouze element selhání je obor názvů kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="705ac-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="705ac-192">SOAP definuje zprávu o chybě jako zprávu, která obsahuje jenom chyby element (element, jehož název je `<env:Fault>`) jako podřízený `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="705ac-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="705ac-193">Obsah elementu selhání mírně mezi SOAP 1.1 a SOAP 1.2, jak je znázorněno na obrázku 1.</span><span class="sxs-lookup"><span data-stu-id="705ac-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="705ac-194">Ale <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> třída normalizuje tyto rozdíly do jednoho objektu modelu:</span><span class="sxs-lookup"><span data-stu-id="705ac-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```  
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
  
 <span data-ttu-id="705ac-195">`Code` Vlastnost odpovídá `env:Code` (nebo `faultCode` v SOAP 1.1) a typ poruchy.</span><span class="sxs-lookup"><span data-stu-id="705ac-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="705ac-196">SOAP 1.2 definuje pět povolených hodnot pro `faultCode` (například odesílatele a příjemce) a definuje `Subcode` element, který může obsahovat libovolnou hodnotu dílčí.</span><span class="sxs-lookup"><span data-stu-id="705ac-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="705ac-197">(Najdete v článku [SOAP 1.2 specifikace](http://go.microsoft.com/fwlink/?LinkId=95176) seznam povolených chybových kódů a jejich významu.) SOAP 1.1 má mechanismus mírně odlišný: definuje čtyři `faultCode` hodnoty (například klient a Server), které lze rozšířit tak, že definujete zcela nové nebo pomocí zápisu s tečkou k vytvoření konkrétnější `faultCodes`, například Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="705ac-197">(See the [SOAP 1.2 specification](http://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="705ac-198">Když pomocí MessageFault program chyb, FaultCode.Name a FaultCode.Namespace mapování název a obor názvů SOAP 1.2 `env:Code` nebo SOAP 1.1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="705ac-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="705ac-199">Se mapuje FaultCode.SubCode `env:Subcode` pro SOAP 1.2 a má hodnotu null pro SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="705ac-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="705ac-200">Měli byste vytvořit nový dílčí kódy chyb (nebo nové kódy chyb při použití protokolu SOAP 1.1) Pokud je zajímavé prostřednictvím kódu programu rozlišit chybu.</span><span class="sxs-lookup"><span data-stu-id="705ac-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="705ac-201">To se podobá je vytvoření nového typu výjimka.</span><span class="sxs-lookup"><span data-stu-id="705ac-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="705ac-202">Neměli byste pomocí zápisu s tečkou s kódy chyb SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="705ac-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="705ac-203">( [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) také nedoporučuje použití tečkami selhání kódu.)</span><span class="sxs-lookup"><span data-stu-id="705ac-203">(The [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
```  
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
  
 <span data-ttu-id="705ac-204">`Reason` Vlastnost odpovídá `env:Reason` (nebo `faultString` v SOAP 1.1) čitelná pro člověka popis podobá zprávy výjimky chybový stav.</span><span class="sxs-lookup"><span data-stu-id="705ac-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="705ac-205">`FaultReason` – Třída (a SOAP `env:Reason/faultString`) má integrovanou podporu pro s více překlady v zájmu globalizace.</span><span class="sxs-lookup"><span data-stu-id="705ac-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```  
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
  
 <span data-ttu-id="705ac-206">Obsah podrobnosti chyby, které jsou zveřejněné na MessageFault pomocí různých metod, včetně `GetDetail` \<T > a `GetReaderAtDetailContents`().</span><span class="sxs-lookup"><span data-stu-id="705ac-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="705ac-207">Podrobnosti o selhání je element neprůhledné pro provedení další podrobnosti o poruchy.</span><span class="sxs-lookup"><span data-stu-id="705ac-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="705ac-208">To je užitečné, pokud je některé libovolný strukturovaných podrobností, která chcete provádění se chyby.</span><span class="sxs-lookup"><span data-stu-id="705ac-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="705ac-209">Generování chyb</span><span class="sxs-lookup"><span data-stu-id="705ac-209">Generating Faults</span></span>  
 <span data-ttu-id="705ac-210">Tato část vysvětluje proces generování chybu v reakci na chybový stav zjištění v kanálu nebo ve vlastnosti zprávy vytvořený kanál.</span><span class="sxs-lookup"><span data-stu-id="705ac-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="705ac-211">Typickým příkladem je odesílání zpět chybu v reakci na žádost o zprávu, která obsahuje neplatná data.</span><span class="sxs-lookup"><span data-stu-id="705ac-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="705ac-212">Při generování chybu, vlastní kanál vůbec Neposílat přímo odolnost, místo toho by měla vyvolat výjimku a nechat vrstvu nad rozhodněte, jestli se má převést této výjimky na chybu a postupy pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="705ac-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="705ac-213">Pro usnadnění tohoto převodu, by měl poskytovat kanál `FaultConverter` implementace, která můžete převést výjimky ve vlastním kanálu pro příslušné selhání.</span><span class="sxs-lookup"><span data-stu-id="705ac-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="705ac-214">`FaultConverter`je definován jako:</span><span class="sxs-lookup"><span data-stu-id="705ac-214">`FaultConverter` is defined as:</span></span>  
  
```  
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
  
 <span data-ttu-id="705ac-215">Každý kanál, který generuje vlastní chyby musí implementovat `FaultConverter` a obnoví v něm volání `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="705ac-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="705ac-216">Vlastní `OnTryCreateFaultMessage` implementace musí buď převést výjimka chybu nebo delegovat na vnitřní kanál `FaultConverter`.</span><span class="sxs-lookup"><span data-stu-id="705ac-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="705ac-217">Pokud je kanál přenos musí převést výjimku nebo delegovat na kodér `FaultConverter` nebo výchozí `FaultConverter` součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="705ac-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .</span></span> <span data-ttu-id="705ac-218">Výchozí hodnota `FaultConverter` převede chyby odpovídající určeného adresování WS a protokolu SOAP zprávy selhání.</span><span class="sxs-lookup"><span data-stu-id="705ac-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="705ac-219">Tady je příklad `OnTryCreateFaultMessage` implementace.</span><span class="sxs-lookup"><span data-stu-id="705ac-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```  
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
  
 <span data-ttu-id="705ac-220">Vyplývá tohoto vzoru je, že výjimky vydané mezi vrstvami pro chybové podmínky, které vyžadují chyb musí obsahovat dostatek informací pro odpovídající generátor selhání vytvoření správné selhání.</span><span class="sxs-lookup"><span data-stu-id="705ac-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="705ac-221">Jako autor vlastní kanál může definovat typy výjimek, které odpovídají podmínky jiné chyby, pokud takové výjimky již neexistují.</span><span class="sxs-lookup"><span data-stu-id="705ac-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="705ac-222">Všimněte si, výjimky procházení vrstvy kanálu by měl komunikovat chybový stav nikoli neprůhledného selhání data.</span><span class="sxs-lookup"><span data-stu-id="705ac-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="705ac-223">Kategorie chyby</span><span class="sxs-lookup"><span data-stu-id="705ac-223">Fault Categories</span></span>  
 <span data-ttu-id="705ac-224">Existují obecně tři kategorie chyb:</span><span class="sxs-lookup"><span data-stu-id="705ac-224">There are generally three categories of faults:</span></span>  
  
1.  <span data-ttu-id="705ac-225">Chyb, které jsou v rámci celý zásobník velkého rozšíření.</span><span class="sxs-lookup"><span data-stu-id="705ac-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="705ac-226">Tyto chyby by mohlo dojít v všechny vrstvy v zásobníku kanál, například InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="705ac-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2.  <span data-ttu-id="705ac-227">Chyb, které může být došlo kdekoli výše určité vrstvy v zásobníku například některé chyby, které se týkají sdružení transakcí nebo role zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="705ac-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3.  <span data-ttu-id="705ac-228">Chyb, které jsou směrované na jedné vrstvy v zásobníku, například chyby jako WS-RM pořadí číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="705ac-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="705ac-229">Kategorie 1.</span><span class="sxs-lookup"><span data-stu-id="705ac-229">Category 1.</span></span> <span data-ttu-id="705ac-230">Chyby jsou obvykle adresování WS a chyb protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="705ac-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="705ac-231">Základní `FaultConverter` třída poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] převede chyby odpovídající selhání zprávy určeného adresování WS a SOAP, není nutné ke zpracování převodu tyto výjimky sami.</span><span class="sxs-lookup"><span data-stu-id="705ac-231">The base `FaultConverter` class provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="705ac-232">Kategorie 2.</span><span class="sxs-lookup"><span data-stu-id="705ac-232">Category 2.</span></span> <span data-ttu-id="705ac-233">Chybám dochází, pokud vrstva přidá vlastnost zprávu, která není zcela využívat zpráva informace, které se vztahují na tuto vrstvu.</span><span class="sxs-lookup"><span data-stu-id="705ac-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="705ac-234">Chyb je možné zjistit později při vyšší vrstvě požádá vlastnost zprávu zpracovat další informace o zprávě.</span><span class="sxs-lookup"><span data-stu-id="705ac-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="705ac-235">Tyto kanály by měla implementovat `GetProperty` zadaný dříve umožňující vyšší vrstvě má být zaslán zpět správné selhání.</span><span class="sxs-lookup"><span data-stu-id="705ac-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="705ac-236">Příkladem je TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="705ac-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="705ac-237">Tato vlastnost je přidána ke zprávě bez plně ověření všechna data v hlavičce (Pokud tak učiníte, může zahrnovat kontaktování koordinátor distribuovaných transakcí (DTC).</span><span class="sxs-lookup"><span data-stu-id="705ac-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="705ac-238">Kategorie 3.</span><span class="sxs-lookup"><span data-stu-id="705ac-238">Category 3.</span></span> <span data-ttu-id="705ac-239">Chyby jsou pouze generované a odeslat pomocí jedné vrstvy v nastavení procesoru.</span><span class="sxs-lookup"><span data-stu-id="705ac-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="705ac-240">Proto všechny výjimky jsou obsažena ve vrstvě.</span><span class="sxs-lookup"><span data-stu-id="705ac-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="705ac-241">Vylepšit konzistenci mezi kanály a usnadnění údržby, měli použít vlastní kanál vzoru dříve určeného ke generování zprávy selhání i pro interní chyby.</span><span class="sxs-lookup"><span data-stu-id="705ac-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="705ac-242">Interpretace přijatých chyb</span><span class="sxs-lookup"><span data-stu-id="705ac-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="705ac-243">Tato část obsahuje pokyny pro generování příslušné výjimky při přijímání zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="705ac-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="705ac-244">Rozhodovací strom pro zpracování na zprávu na všechny vrstvy v zásobníku vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="705ac-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1.  <span data-ttu-id="705ac-245">Pokud je zpráva Neplatná za vrstvy, vrstvě měli udělat jeho zpracování "Neplatná zpráva".</span><span class="sxs-lookup"><span data-stu-id="705ac-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="705ac-246">Toto zpracování je specifická pro vrstvy, ale mohou obsahovat vyřazení se zpráva trasování, nebo došlo k výjimce, který získá převést na chybu.</span><span class="sxs-lookup"><span data-stu-id="705ac-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="705ac-247">Mezi příklady patří zabezpečení přijímání zprávy, které nejsou řádně zabezpečená, nebo RM přijímání zprávy s chybné pořadové číslo.</span><span class="sxs-lookup"><span data-stu-id="705ac-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2.  <span data-ttu-id="705ac-248">Pokud zpráva je zprávu o chybě, která se vztahuje konkrétně na vrstvu a zpráva není smysluplný mimo interakce vrstvy, by měla řídit vrstvy, jinak hodnota chybový stav.</span><span class="sxs-lookup"><span data-stu-id="705ac-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="705ac-249">Příkladem je selhání RM pořadí odmítl smysl na vrstvy výše RM kanál a který znamená přerušením RM kanálu a byla vrácena z čekající operace.</span><span class="sxs-lookup"><span data-stu-id="705ac-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3.  <span data-ttu-id="705ac-250">Zpráva, jinak hodnota má být vrácen z Request() nebo Receive().</span><span class="sxs-lookup"><span data-stu-id="705ac-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="705ac-251">To zahrnuje případech, kdy vrstvě rozpozná chybu, ale poruchy právě označuje, že žádost se nezdařila a neznamená přerušením kanálu a byla vrácena z čekající operace.</span><span class="sxs-lookup"><span data-stu-id="705ac-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="705ac-252">Pokud chcete zlepšit použitelnost v takovém případě, by měla implementovat vrstvě `GetProperty<FaultConverter>` a vrátit `FaultConverter` odvozené třídy, které můžete převést selhání výjimku přepsáním `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="705ac-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="705ac-253">Následující objektový model podporuje převod zprávy k výjimkám:</span><span class="sxs-lookup"><span data-stu-id="705ac-253">The following object model supports converting messages to exceptions:</span></span>  
  
```  
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
  
 <span data-ttu-id="705ac-254">Můžete implementovat vrstvy kanálu `GetProperty<FaultConverter>` pro podporu převodu chybové zprávy k výjimkám.</span><span class="sxs-lookup"><span data-stu-id="705ac-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="705ac-255">Chcete-li to provést, přepište `OnTryCreateException` a zkontrolovat zprávu chyby.</span><span class="sxs-lookup"><span data-stu-id="705ac-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="705ac-256">Pokud rozpoznána, provést převod, jinak požádejte vnitřní kanál ji převést.</span><span class="sxs-lookup"><span data-stu-id="705ac-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="705ac-257">Přenosové kanály by měly delegovat do `FaultConverter.GetDefaultFaultConverter` získat výchozí SOAP, WS-Addressing FaultConverter.</span><span class="sxs-lookup"><span data-stu-id="705ac-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="705ac-258">Typická implementace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="705ac-258">A typical implementation looks like this:</span></span>  
  
```  
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
  
 <span data-ttu-id="705ac-259">Pro konkrétní chyby podmínky, které mají odlišné obnovení scénáře, zvažte možnost definice odvozených tříd z `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="705ac-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="705ac-260">Atribut MustUnderstand zpracování</span><span class="sxs-lookup"><span data-stu-id="705ac-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="705ac-261">SOAP definuje k obecné chybě signalizace, že požadovaná hlavička nebyla rozpoznaná příjemce.</span><span class="sxs-lookup"><span data-stu-id="705ac-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="705ac-262">Toto selhání se označuje jako `mustUnderstand` selhání.</span><span class="sxs-lookup"><span data-stu-id="705ac-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="705ac-263">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], nikdy generovat vlastní kanály `mustUnderstand` chyb.</span><span class="sxs-lookup"><span data-stu-id="705ac-263">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="705ac-264">Místo toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispečera, která se nachází v horní části [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikačního balíku, zkontroluje, který všechny hlavičky, které byly označeny jako MustUndestand = true se rozumí základní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="705ac-264">Instead, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Dispatcher, which is located at the top of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication stack, checks to see that all headers that were marked as MustUndestand=true were understood by the underlying stack.</span></span> <span data-ttu-id="705ac-265">Pokud žádné nebyly porozuměl jsem jim `mustUnderstand` se v tomto bodě vygeneruje chyby.</span><span class="sxs-lookup"><span data-stu-id="705ac-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="705ac-266">(Můžete vybrat uživatel pro tento vypnout `mustUnderstand` zpracování a aplikace přijímat všechny hlavičky zpráv.</span><span class="sxs-lookup"><span data-stu-id="705ac-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="705ac-267">In that Case aplikace zodpovídá za provádění `mustUnderstand` zpracování.) Vygenerovaný selhání obsahuje hlavičku NotUnderstood, která obsahuje názvy všech záhlaví s MustUnderstand = true, které nebyly rozumí.</span><span class="sxs-lookup"><span data-stu-id="705ac-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="705ac-268">Pokud protokol kanál odešle vlastní hlavičku s MustUnderstand = true a přijímá `mustUnderstand` selhání, se musí zjistit, jestli je kvůli hlavička ho odeslaná této chyby.</span><span class="sxs-lookup"><span data-stu-id="705ac-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="705ac-269">Existují dva členy na `MessageFault` třídu, která jsou užitečné pro toto:</span><span class="sxs-lookup"><span data-stu-id="705ac-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="705ac-270">`IsMustUnderstandFault`Vrátí `true` Pokud je odolnost `mustUnderstand` selhání.</span><span class="sxs-lookup"><span data-stu-id="705ac-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="705ac-271">`WasHeaderNotUnderstood`Vrátí `true` Pokud hlavička se zadaným názvem a oborem názvů je součástí selhání jako hlavičku NotUnderstood.</span><span class="sxs-lookup"><span data-stu-id="705ac-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="705ac-272">Funkce `false`.</span><span class="sxs-lookup"><span data-stu-id="705ac-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="705ac-273">Pokud je kanál, který vysílá hlavičku, která je označena MustUnderstand = true, pak tuto vrstvu by také implementovat vzor rozhraní API pro generování výjimek a měli převést `mustUnderstand` chyby způsobené této hlavičky užitečnější výjimce, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="705ac-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="705ac-274">Trasování</span><span class="sxs-lookup"><span data-stu-id="705ac-274">Tracing</span></span>  
 <span data-ttu-id="705ac-275">Rozhraní .NET Framework poskytuje mechanismus pro trasování spuštění programu jako způsob, jak Diagnostika produkční žádosti o podporu nebo přerušované problémy, které není možné právě připojit ladicí program a krokovat kód.</span><span class="sxs-lookup"><span data-stu-id="705ac-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="705ac-276">Základní součásti služby tento mechanismus jsou v <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů a obsahovat:</span><span class="sxs-lookup"><span data-stu-id="705ac-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
-   <span data-ttu-id="705ac-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj informací trasování, které má být zapsán <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, což je abstraktní základní třídu pro konkrétní naslouchací procesy, které přijímají informace k trasování z <xref:System.Diagnostics.TraceSource> a výstup do cílového umístění, specifické pro naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="705ac-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="705ac-278">Například <xref:System.Diagnostics.XmlWriterTraceListener> výstupy trasování informace do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="705ac-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="705ac-279">Nakonec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, který umožňuje řídit podrobností trasování uživatelů aplikace a je obvykle zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="705ac-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
-   <span data-ttu-id="705ac-280">Kromě základních komponent, můžete použít [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení a hledání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view and search [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] traces.</span></span> <span data-ttu-id="705ac-281">Nástroj je určený speciálně pro trasovací soubory generované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a zapsány pomocí <xref:System.Diagnostics.XmlWriterTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="705ac-281">The tool is designed specifically for trace files generated by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="705ac-282">Následující obrázek ukazuje různé součásti účastnící se trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="705ac-283">![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="705ac-283">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="705ac-284">Trasování z vlastního kanálu</span><span class="sxs-lookup"><span data-stu-id="705ac-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="705ac-285">Vlastní kanály měli zapsat trasování zprávy jako pomůcku při diagnostikování problémů, když není možné připojit ladicí program pro běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="705ac-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="705ac-286">To zahrnuje dvě úlohy nejvyšších úrovní: vytváření instancí <xref:System.Diagnostics.TraceSource> a volání její metody k zápisu trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="705ac-287">Při vytváření instance <xref:System.Diagnostics.TraceSource>, zadáte řetězec stane název tohoto zdroje.</span><span class="sxs-lookup"><span data-stu-id="705ac-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="705ac-288">Tento název slouží ke konfiguraci zdroj trasování (povolit nebo zakázat nebo nastavení trasování úroveň).</span><span class="sxs-lookup"><span data-stu-id="705ac-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="705ac-289">Zobrazuje se taky v samotné výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="705ac-290">Vlastní kanály by měl použít název jedinečný zdroj pomohou čtečky výstup trasování pochopit, kde informace trasování pocházejí z.</span><span class="sxs-lookup"><span data-stu-id="705ac-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="705ac-291">Pomocí názvu sestavení, který zapisuje informace jako název zdroje trasování je běžnou praxí.</span><span class="sxs-lookup"><span data-stu-id="705ac-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="705ac-292">Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.ServiceModel se používá jako zdroj trasování pro zapsaných informací z System.ServiceModel sestavení.</span><span class="sxs-lookup"><span data-stu-id="705ac-292">For example, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="705ac-293">Až budete mít zdroj trasování, zavoláte jeho <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metody k zápisu trasování položek pro naslouchací procesy trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="705ac-294">Pro každou položku trasování napíšete, budete muset klasifikovat jako jeden z typů událostí, které jsou definované v typu události <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="705ac-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="705ac-295">Tato klasifikace a nastavení úrovně trasování v konfiguraci určit, zda je položka sledování výstup do naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="705ac-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="705ac-296">Například v konfiguraci k nastavení úrovně trasování `Warning` umožňuje `Warning`, `Error` a `Critical` trasování položky k zapsání ale bloky informace a podrobné záznamy.</span><span class="sxs-lookup"><span data-stu-id="705ac-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="705ac-297">Tady je příklad vytvoření instance zdroj trasování a zápis na položku na úrovni informace:</span><span class="sxs-lookup"><span data-stu-id="705ac-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="705ac-298">Důrazně doporučujeme, že zadáváte název zdroje trasování, které jsou jedinečné pro vaše vlastní kanál pomohou čtenářům výstup trasování pochopit, odkud pochází výstup.</span><span class="sxs-lookup"><span data-stu-id="705ac-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="705ac-299">Integrace s prohlížeče trasování</span><span class="sxs-lookup"><span data-stu-id="705ac-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="705ac-300">Trasování generované kanál může být výstup ve formátu přečíst [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pomocí <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="705ac-301">Toto není něco, jako vývojář kanál, musíte udělat.</span><span class="sxs-lookup"><span data-stu-id="705ac-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="705ac-302">Místo toho je uživatel aplikace (nebo osoby, řešení potíží s aplikace), které je konfigurace této naslouchací proces trasování v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="705ac-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="705ac-303">Například následující konfigurace výstupy trasování informace z obou <xref:System.ServiceModel?displayProperty=nameWithType> a `Microsoft.Samples.Udp` do souboru s názvem `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="705ac-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="705ac-304">Trasování strukturovaných dat</span><span class="sxs-lookup"><span data-stu-id="705ac-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="705ac-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>má <xref:System.Diagnostics.TraceSource.TraceData%2A> metody, která přijímá jeden nebo více objektů, které mají být zahrnuty v položce trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="705ac-306">Obecně <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda je volána na každém objektu a výsledný řetězec je zapsán v rámci položky trasování.</span><span class="sxs-lookup"><span data-stu-id="705ac-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="705ac-307">Při použití <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> výstup trasování, můžete předat <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako datový objekt k <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="705ac-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="705ac-308">Výsledná položka trasování obsahuje XML poskytované <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="705ac-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="705ac-309">Tady je příklad položku s XML data aplikací:</span><span class="sxs-lookup"><span data-stu-id="705ac-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="705ac-310">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Prohlížeče trasování rozumí schéma `TraceRecord` element uvedený výše a extrahuje data z její podřízené elementy a zobrazí v tabulkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="705ac-310">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="705ac-311">Kanál používejte toto schéma při trasování data strukturovaných aplikací pomoci uživatelům Svctraceviewer.exe číst data.</span><span class="sxs-lookup"><span data-stu-id="705ac-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
