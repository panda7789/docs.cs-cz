---
title: Zpracování výjimek a chyb
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: f2042bac30ee84530c0da9c30193919dfb99a608
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655003"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="db94b-102">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="db94b-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="db94b-103">Výjimky se používají k předání chyby místně v rámci služby nebo implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="db94b-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="db94b-104">Chyby, na druhé straně, se používají k předání chyby přes hranice služeb, jako například ze serveru klientovi nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="db94b-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="db94b-105">Kromě chyb přenosové kanály často používají mechanismy specifické pro přenos komunikace chyb na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="db94b-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="db94b-106">Například přenos pomocí protokolu HTTP používá stavové kódy, jako je například 404 ke komunikaci neexistující adresa URL koncového bodu (neexistuje žádný koncový bod má být zaslán zpět chybu).</span><span class="sxs-lookup"><span data-stu-id="db94b-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="db94b-107">Tento dokument se skládá z tři oddíly, které poskytují pokyny pro autory vlastního kanálu.</span><span class="sxs-lookup"><span data-stu-id="db94b-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="db94b-108">První část obsahuje pokyny k kdy a jak definovat a vyvolávat výjimky.</span><span class="sxs-lookup"><span data-stu-id="db94b-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="db94b-109">Druhá část obsahuje pokyny týkající se vytváření a využívání chyb.</span><span class="sxs-lookup"><span data-stu-id="db94b-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="db94b-110">Třetí část vysvětluje, jak poskytnout informace o trasování pro řešení potíží s běžící aplikací uživatele vlastního kanálu.</span><span class="sxs-lookup"><span data-stu-id="db94b-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="db94b-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="db94b-111">Exceptions</span></span>  
 <span data-ttu-id="db94b-112">Mějte na paměti při vyvolání výjimky dvě věci: Nejprve musí být typu, který umožňuje zapisovat správný kód, který může reagovat odpovídajícím způsobem na výjimku.</span><span class="sxs-lookup"><span data-stu-id="db94b-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="db94b-113">Za druhé má poskytnout dostatek informací pro uživatele k pochopení toho, co nefunguje, dopad selhání a jak ho opravit.</span><span class="sxs-lookup"><span data-stu-id="db94b-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="db94b-114">Následující části poskytují pokyny týkající se typy výjimek a zprávy pro kanály Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="db94b-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="db94b-115">Je také obecné pokyny k jeho výjimek v rozhraní .NET v pokyny návrhu pro výjimky dokumentu.</span><span class="sxs-lookup"><span data-stu-id="db94b-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="db94b-116">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="db94b-116">Exception Types</span></span>  
 <span data-ttu-id="db94b-117">Všechny výjimky vyvolané kanály musí být buď <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, nebo typ odvozený od <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="db94b-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="db94b-118">(Například výjimky <xref:System.ObjectDisposedException> může také být vyvolána výjimka, ale pouze pro označení, že volající kód má potenciálně nebezpečného kanál.</span><span class="sxs-lookup"><span data-stu-id="db94b-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="db94b-119">Pokud se používá kanál, se musí pouze vyvolat dané výjimky.) WCF obsahuje sedm typy výjimek, které jsou odvozeny z <xref:System.ServiceModel.CommunicationException> a jsou navržené pro kanály.</span><span class="sxs-lookup"><span data-stu-id="db94b-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="db94b-120">Existují jiné <xref:System.ServiceModel.CommunicationException>-odvozené výjimky, které jsou navrženy pro použití jinými částmi systému.</span><span class="sxs-lookup"><span data-stu-id="db94b-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="db94b-121">Tyto typy výjimek jsou:</span><span class="sxs-lookup"><span data-stu-id="db94b-121">These exception types are:</span></span>  
  
|<span data-ttu-id="db94b-122">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="db94b-122">Exception Type</span></span>|<span data-ttu-id="db94b-123">Význam</span><span class="sxs-lookup"><span data-stu-id="db94b-123">Meaning</span></span>|<span data-ttu-id="db94b-124">Obsah v popisu vnitřní výjimky</span><span class="sxs-lookup"><span data-stu-id="db94b-124">Inner Exception Content</span></span>|<span data-ttu-id="db94b-125">Strategie zotavení</span><span class="sxs-lookup"><span data-stu-id="db94b-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="db94b-126">Zadaná adresa koncového bodu pro naslouchání je již používán.</span><span class="sxs-lookup"><span data-stu-id="db94b-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="db94b-127">Pokud jsou k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="db94b-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="db94b-128">Např.</span><span class="sxs-lookup"><span data-stu-id="db94b-128">For example.</span></span> <span data-ttu-id="db94b-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, nebo <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="db94b-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="db94b-130">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="db94b-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="db94b-131">Proces není povolený přístup k adresu koncového bodu, který je zadán pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="db94b-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="db94b-132">Pokud jsou k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="db94b-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="db94b-133">Například <xref:System.IO.PipeException>, nebo <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="db94b-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="db94b-134">Zkuste s jinými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="db94b-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="db94b-135"><xref:System.ServiceModel.ICommunicationObject> Používá je v chybovém stavu (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="db94b-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="db94b-136">Všimněte si, že když objekt s více čekající volání přejde do stavu chyba pouze jedno volání, vyvolá výjimku, týkající se selhání a zbytek throw volání <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="db94b-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="db94b-137">Tato výjimka je obvykle vyvolána, protože aplikace overlooks některé výjimky a pokusí se použít objekt již chybnou pravděpodobně ve vlákně, než která byla zachycena výjimka původní.</span><span class="sxs-lookup"><span data-stu-id="db94b-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="db94b-138">Pokud jsou k dispozici obsahuje podrobné informace o vnitřní výjimce.</span><span class="sxs-lookup"><span data-stu-id="db94b-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="db94b-139">Vytvořte nový objekt.</span><span class="sxs-lookup"><span data-stu-id="db94b-139">Create a new object.</span></span> <span data-ttu-id="db94b-140">Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> k selhání na prvním místě, může být jiné práce potřebné k obnovení.</span><span class="sxs-lookup"><span data-stu-id="db94b-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="db94b-141"><xref:System.ServiceModel.ICommunicationObject> Používá byla přerušena. (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="db94b-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="db94b-142">Podobně jako <xref:System.ServiceModel.CommunicationObjectFaultedException>, jeho výjimka označuje, že aplikace volala <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na objekt, případně z jiného vlákna, a objekt již není použitelné z tohoto důvodu.</span><span class="sxs-lookup"><span data-stu-id="db94b-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="db94b-143">Pokud jsou k dispozici obsahuje podrobné informace o vnitřní výjimce.</span><span class="sxs-lookup"><span data-stu-id="db94b-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="db94b-144">Vytvořte nový objekt.</span><span class="sxs-lookup"><span data-stu-id="db94b-144">Create a new object.</span></span> <span data-ttu-id="db94b-145">Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> přerušit na prvním místě, může být jiné práce potřebné k obnovení.</span><span class="sxs-lookup"><span data-stu-id="db94b-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="db94b-146">Vzdálený koncový bod cíl nenaslouchá.</span><span class="sxs-lookup"><span data-stu-id="db94b-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="db94b-147">To může být následek libovolné části adresu koncového bodu je nesprávná, nevyřešitelná nebo koncový bod se dolů.</span><span class="sxs-lookup"><span data-stu-id="db94b-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="db94b-148">Mezi příklady patří chybu DNS, správce fronty není k dispozici a služba není spuštěná.</span><span class="sxs-lookup"><span data-stu-id="db94b-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="db94b-149">Vnitřní výjimka obsahuje podrobné informace, typicky ze základní přenos.</span><span class="sxs-lookup"><span data-stu-id="db94b-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="db94b-150">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="db94b-150">Try a different address.</span></span> <span data-ttu-id="db94b-151">Alternativně může odesílatel chvíli počkejte a zkuste to znovu v případě, že služba se dolů</span><span class="sxs-lookup"><span data-stu-id="db94b-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="db94b-152">Komunikační protokoly, jak je popsáno v zásad koncového bodu se neshoda mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="db94b-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="db94b-153">Například rámců Neshoda typu obsahu nebo překročila se maximální počet zpráv velikost.</span><span class="sxs-lookup"><span data-stu-id="db94b-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="db94b-154">Pokud jsou k dispozici poskytuje další informace o chybě určitý protokol.</span><span class="sxs-lookup"><span data-stu-id="db94b-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="db94b-155">Například <xref:System.ServiceModel.QuotaExceededException> je vnitřní výjimka, pokud příčina chyby je vyšší než MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="db94b-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="db94b-156">Obnovení: Zajištění odesílatele a přijaté protokolu, které odpovídají nastavení.</span><span class="sxs-lookup"><span data-stu-id="db94b-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="db94b-157">Jedním ze způsobů, provedete to tak je znovu importovat metadata koncový bod služby (zásady) a znovu vytvořit kanál pomocí generovaného vazby.</span><span class="sxs-lookup"><span data-stu-id="db94b-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="db94b-158">Vzdálený koncový bod naslouchá, ale není připravená pro zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="db94b-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="db94b-159">Pokud jsou k dispozici, poskytuje vnitřní výjimka nastala chyba protokolu SOAP nebo podrobnosti o chybě na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="db94b-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="db94b-160">Obnovení: Počkejte a zkuste operaci zopakovat později.</span><span class="sxs-lookup"><span data-stu-id="db94b-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="db94b-161">Operaci se nepodařilo dokončit v časovém limitu.</span><span class="sxs-lookup"><span data-stu-id="db94b-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="db94b-162">Může poskytnout podrobnosti o časový limit.</span><span class="sxs-lookup"><span data-stu-id="db94b-162">May provide details about the timeout.</span></span>|<span data-ttu-id="db94b-163">Počkejte a zkuste operaci zopakovat později.</span><span class="sxs-lookup"><span data-stu-id="db94b-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="db94b-164">Definujte nový typ výjimky, pouze v případě, že tento typ odpovídá strategii pro konkrétní zotavení odlišné od všech existujících typů výjimek.</span><span class="sxs-lookup"><span data-stu-id="db94b-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="db94b-165">Pokud definujete nový typ výjimky, musí být odvozen od <xref:System.ServiceModel.CommunicationException> nebo jeden z jeho odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="db94b-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="db94b-166">Zprávy o výjimkách</span><span class="sxs-lookup"><span data-stu-id="db94b-166">Exception Messages</span></span>  
 <span data-ttu-id="db94b-167">Zprávy o výjimkách, které jsou zaměřeny na uživatele není program, se musí poskytovat dostatečné informace umožňující uživateli pochopit a vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="db94b-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="db94b-168">Jsou tři základní části zprávy dobré výjimka:</span><span class="sxs-lookup"><span data-stu-id="db94b-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="db94b-169">Co se přihodilo.</span><span class="sxs-lookup"><span data-stu-id="db94b-169">What happened.</span></span> <span data-ttu-id="db94b-170">Zadejte jasný popis problému pomocí termínů, které se týkají prostředí uživatele.</span><span class="sxs-lookup"><span data-stu-id="db94b-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="db94b-171">Například by zpráva chybná výjimky "Neplatný konfigurační oddíl".</span><span class="sxs-lookup"><span data-stu-id="db94b-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="db94b-172">Kvůli tomu uživatele zajímá vás, jaké konfiguračního oddílu je nesprávný a proč je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="db94b-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="db94b-173">Vylepšené zprávy by "Neplatný konfigurační oddíl \<customBinding >".</span><span class="sxs-lookup"><span data-stu-id="db94b-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="db94b-174">Zpráva ještě lepší by bylo "nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenosu s názvem myTransport".</span><span class="sxs-lookup"><span data-stu-id="db94b-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="db94b-175">To je velmi konkrétní zprávu pomocí podmínek a názvy, které uživatele, snadno zjistíte v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="db94b-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="db94b-176">Existují však ještě několik klíčových komponent chybí.</span><span class="sxs-lookup"><span data-stu-id="db94b-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="db94b-177">Význam chybu.</span><span class="sxs-lookup"><span data-stu-id="db94b-177">The significance of the error.</span></span> <span data-ttu-id="db94b-178">Pokud zpráva s oznámením jasně znamená chybu, uživatel by mohla zajímat, jestli se o závažnou chybu nebo pokud se to dá ignorovat.</span><span class="sxs-lookup"><span data-stu-id="db94b-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="db94b-179">Obecně platí by měl vést zprávy s význam nebo závažnosti chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="db94b-180">Aby se zvýšil z předchozího příkladu, může být zpráva "hostitel služby se nepodařilo otevřít kvůli chybě v konfiguraci: Nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenosu s názvem myTransport ".</span><span class="sxs-lookup"><span data-stu-id="db94b-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="db94b-181">Jak uživatel má problém.</span><span class="sxs-lookup"><span data-stu-id="db94b-181">How the user should correct the problem.</span></span> <span data-ttu-id="db94b-182">Nejdůležitější část zprávy pomáhá uživatele vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="db94b-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="db94b-183">Zpráva by měl obsahovat některé pokyny nebo nápovědu, jak zkontrolovat nebo opravit a odstranění problému.</span><span class="sxs-lookup"><span data-stu-id="db94b-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="db94b-184">Například "hostitel služby se nepodařilo otevřít kvůli chybě v konfiguraci: Nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenosu s názvem myTransport.</span><span class="sxs-lookup"><span data-stu-id="db94b-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="db94b-185">Ujistěte se, že existuje pouze jeden přenosu ve vazbě".</span><span class="sxs-lookup"><span data-stu-id="db94b-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="db94b-186">Komunikaci chyb</span><span class="sxs-lookup"><span data-stu-id="db94b-186">Communicating Faults</span></span>  
 <span data-ttu-id="db94b-187">Protokol SOAP 1.1 a SOAP 1.2 definovat strukturu specifické pro chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="db94b-188">Existuje několik rozdílů mezi dvěma specifikace, ale obecně typy zpráv a objekt MessageFault se používají k vytváření a využívání chyb.</span><span class="sxs-lookup"><span data-stu-id="db94b-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="db94b-189">![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1. 1AndSOAP1 2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="db94b-189">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="db94b-190">Ze SOAP 1.2 selhání (vlevo) a Chyba protokolu SOAP 1.1 (vpravo).</span><span class="sxs-lookup"><span data-stu-id="db94b-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="db94b-191">Upozorňujeme, že v protokolu SOAP 1.1 pouze element selhání oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="db94b-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="db94b-192">SOAP definuje zprávu o chybě jako zprávu, která obsahuje jenom chyby element (element, jehož název je `<env:Fault>`) jako podřízený objekt `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="db94b-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="db94b-193">Obsah elementu selhání mírně mezi SOAP 1.1 a SOAP 1.2, jak je znázorněno na obrázku 1.</span><span class="sxs-lookup"><span data-stu-id="db94b-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="db94b-194">Ale <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> normalizuje tyto rozdíly do modelu jeden objekt třídy:</span><span class="sxs-lookup"><span data-stu-id="db94b-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
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
  
 <span data-ttu-id="db94b-195">`Code` Odpovídá vlastnosti `env:Code` (nebo `faultCode` v protokolu SOAP 1.1) a identifikuje typ chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="db94b-196">Protokol SOAP 1.2 definuje pět povolené hodnoty pro `faultCode` (například odesílatel a příjemce) a definuje `Subcode` element, který může obsahovat libovolnou hodnotu podřízeného.</span><span class="sxs-lookup"><span data-stu-id="db94b-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="db94b-197">(Viz [specifikace SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=95176) seznam povolených chybových kódů a jejich význam.) Protokol SOAP 1.1 má mírně odlišné mechanismus: Definuje čtyři `faultCode` hodnoty (například klient a Server), které můžete rozšířit definováním zcela nové značky nebo vytvořte konkrétnější pomocí zápisu s tečkou `faultCodes`, například Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="db94b-197">(See the [SOAP 1.2 specification](https://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="db94b-198">Když použijete objekt MessageFault na chyby programu, FaultCode.Name a FaultCode.Namespace mapuje na název a obor názvů SOAP 1.2 `env:Code` nebo SOAP 1.1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="db94b-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="db94b-199">Mapuje FaultCode.SubCode `env:Subcode` pro SOAP 1.2 a má hodnotu null. pro protokol SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="db94b-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="db94b-200">Měli byste vytvořit nový dílčí kódy chyb (nebo nové kódy chyb při použití protokolu SOAP 1.1) Pokud je zajímavé programově rozlišit chybu.</span><span class="sxs-lookup"><span data-stu-id="db94b-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="db94b-201">Toto je analogická k vytvoření nového typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="db94b-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="db94b-202">Neměli byste pomocí zápisu s tečkou s kódy chyb protokolu SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="db94b-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="db94b-203">( [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) také odrazuje od pomocí zápisu s tečkou kód chyby.)</span><span class="sxs-lookup"><span data-stu-id="db94b-203">(The [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
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
  
 <span data-ttu-id="db94b-204">`Reason` Odpovídá vlastnosti `env:Reason` (nebo `faultString` v protokolu SOAP 1.1) čitelný popis podobná zpráva výjimce chybový stav.</span><span class="sxs-lookup"><span data-stu-id="db94b-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="db94b-205">`FaultReason` Třídu (a SOAP `env:Reason/faultString`) obsahuje integrovanou podporu s více překlady větší globalizace.</span><span class="sxs-lookup"><span data-stu-id="db94b-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
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
  
 <span data-ttu-id="db94b-206">Obsah podrobnosti o selhání jsou zveřejněné na objekt MessageFault pomocí různých metod, včetně `GetDetail` \<T > a `GetReaderAtDetailContents`().</span><span class="sxs-lookup"><span data-stu-id="db94b-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="db94b-207">Detail chyby se element neprůhledné pro další podrobnosti o chybu provádění.</span><span class="sxs-lookup"><span data-stu-id="db94b-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="db94b-208">To je užitečné, pokud je některé libovolného strukturovaných podrobností, které chcete provést s chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="db94b-209">Generování chyb</span><span class="sxs-lookup"><span data-stu-id="db94b-209">Generating Faults</span></span>  
 <span data-ttu-id="db94b-210">Tato část vysvětluje proces generuje chybu v reakci na chybový stav zjištění v kanálu nebo do zprávy vlastnost vytvořený kanál.</span><span class="sxs-lookup"><span data-stu-id="db94b-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="db94b-211">Typickým příkladem je odesílá zpět chybu v reakci na zprávu požadavku, která obsahuje neplatná data.</span><span class="sxs-lookup"><span data-stu-id="db94b-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="db94b-212">Při generování chybu, vlastním kanálu by neměl přímo odeslat chyby, místo toho by měla vyvolat výjimku a nechat vrstvu nad rozhodnout, jestli se má převést tuto výjimku na chybu a jak ji odeslat.</span><span class="sxs-lookup"><span data-stu-id="db94b-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="db94b-213">Pro tento převod, by měly poskytnout kanál `FaultConverter` implementace, která můžete převést výjimku vyvolanou ve vlastním kanálu pro příslušné chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="db94b-214">`FaultConverter` je definována takto:</span><span class="sxs-lookup"><span data-stu-id="db94b-214">`FaultConverter` is defined as:</span></span>  
  
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
  
 <span data-ttu-id="db94b-215">Každý kanál, který generuje vlastní chyby musí implementovat `FaultConverter` a vrátit ji z volání `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="db94b-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="db94b-216">Vlastní `OnTryCreateFaultMessage` implementace musí převést do srozumitelného chybu nebo delegovat do vnitřního kanálu `FaultConverter`.</span><span class="sxs-lookup"><span data-stu-id="db94b-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="db94b-217">Pokud je kanál přenosu musí, buď ji převést do srozumitelného nebo delegovat kodér `FaultConverter` nebo výchozí hodnotu `FaultConverter` součástí WCF.</span><span class="sxs-lookup"><span data-stu-id="db94b-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="db94b-218">Výchozí hodnota `FaultConverter` převede chyby odpovídající chybové zprávy určené WS-Addressing a SOAP.</span><span class="sxs-lookup"><span data-stu-id="db94b-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="db94b-219">Tady je příklad `OnTryCreateFaultMessage` implementace.</span><span class="sxs-lookup"><span data-stu-id="db94b-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
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
  
 <span data-ttu-id="db94b-220">Důsledkem tohoto modelu je, že výjimky vyvolané mezi vrstvami pro chybové podmínky, které vyžadují chyby musí obsahovat dostatek informací pro odpovídající generátor selhání vytvoření správné chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="db94b-221">Jako vlastní kanál Autor můžete definovat typy výjimek, které odpovídají různých chybových podmínek, je-li tyto výjimky již neexistují.</span><span class="sxs-lookup"><span data-stu-id="db94b-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="db94b-222">Všimněte si, že byste neprůhledné odolnost dat. chybová podmínka spíše než komunikovat výjimky procházení vrstvám kanálu.</span><span class="sxs-lookup"><span data-stu-id="db94b-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="db94b-223">Kategorie chyby</span><span class="sxs-lookup"><span data-stu-id="db94b-223">Fault Categories</span></span>  
 <span data-ttu-id="db94b-224">Existují obecně tři kategorie chyb:</span><span class="sxs-lookup"><span data-stu-id="db94b-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="db94b-225">Chyby, které se objevují v rámci celý zásobník.</span><span class="sxs-lookup"><span data-stu-id="db94b-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="db94b-226">Tyto chyby by mohlo dojít v libovolné vrstvě v zásobníku kanál, třeba InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="db94b-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="db94b-227">Chyby, které mohou být došlo k kdekoli nad určitým vrstvou v zásobníku například některé chyby, které se týkají sdružení transakcí nebo k rolím zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db94b-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="db94b-228">Chyby, které jsou směrované na jedné vrstvy v zásobníku, například chyby, jako je číslo chyby WS-RM pořadí.</span><span class="sxs-lookup"><span data-stu-id="db94b-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="db94b-229">Kategorie 1.</span><span class="sxs-lookup"><span data-stu-id="db94b-229">Category 1.</span></span> <span data-ttu-id="db94b-230">Chyby jsou obvykle WS-Addressing a chyb SOAP.</span><span class="sxs-lookup"><span data-stu-id="db94b-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="db94b-231">Základní `FaultConverter` třídy poskytované službou WCF chyby převede odpovídající chybové zprávy specifikované WS-Addressing a SOAP, není nutné ke zpracování převodu těchto výjimek sami.</span><span class="sxs-lookup"><span data-stu-id="db94b-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="db94b-232">Kategorie 2.</span><span class="sxs-lookup"><span data-stu-id="db94b-232">Category 2.</span></span> <span data-ttu-id="db94b-233">K chybám dochází při vrstvy přidá vlastnost na zprávu, která úplně nespotřebovává zpráva informace, které se vztahují k této vrstvě.</span><span class="sxs-lookup"><span data-stu-id="db94b-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="db94b-234">Chyby může později zjistit, když vyšší vrstvu zeptá vlastnost zprávy zpracovávat další informace o zprávě.</span><span class="sxs-lookup"><span data-stu-id="db94b-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="db94b-235">Tyto kanály by měly implementovat `GetProperty` zadaný dříve umožňuje vyšší vrstvě má být zaslán zpět správné chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="db94b-236">Příkladem je TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="db94b-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="db94b-237">Tato vlastnost se přidá do zprávy bez plně ověřování všechna data v hlavičce (díky tomu může zahrnovat kontaktování koordinátor distribuovaných transakcí (DTC).</span><span class="sxs-lookup"><span data-stu-id="db94b-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="db94b-238">Kategorie 3.</span><span class="sxs-lookup"><span data-stu-id="db94b-238">Category 3.</span></span> <span data-ttu-id="db94b-239">Chyby jsou pouze vygenerovat a odeslat pomocí jedné vrstvy v procesoru.</span><span class="sxs-lookup"><span data-stu-id="db94b-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="db94b-240">Proto všechny výjimky jsou obsaženy v rámci vrstvy.</span><span class="sxs-lookup"><span data-stu-id="db94b-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="db94b-241">Vylepšit konzistenci mezi kanály a snadné údržby, měli by používat vlastní kanál vzoru určenému dříve generovat selhání i pro interní chyby.</span><span class="sxs-lookup"><span data-stu-id="db94b-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="db94b-242">Interpretace přijatých chyb</span><span class="sxs-lookup"><span data-stu-id="db94b-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="db94b-243">Tato část obsahuje pokyny pro generování vhodná výjimka při přijímání zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="db94b-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="db94b-244">Rozhodovací strom pro zpracování zprávy v každé vrstvě v zásobníku je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="db94b-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="db94b-245">Pokud zpráva není platný za vrstvu, vrstvy proveďte jeho zpracování "Neplatná zpráva".</span><span class="sxs-lookup"><span data-stu-id="db94b-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="db94b-246">Toto zpracování je specifická pro vrstvy, ale mohou obsahovat vyřazením zprávy trasování, nebo došlo k výjimce, která získá převedeny na chybu.</span><span class="sxs-lookup"><span data-stu-id="db94b-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="db94b-247">Mezi příklady patří zabezpečení, které přijímají zprávy, která nejsou řádně zabezpečená nebo RM přijetí zprávy s chybné pořadové číslo.</span><span class="sxs-lookup"><span data-stu-id="db94b-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="db94b-248">Jinak Pokud zpráva je chybová zpráva, která se vztahuje konkrétně k vrstvě a zpráva není smysluplné mimo interakce vrstvy, vrstvě by měl zpracovat chybový stav.</span><span class="sxs-lookup"><span data-stu-id="db94b-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="db94b-249">Příkladem je selhání bylo odmítnuto pořadí RM, který nemá význam do vrstvy nad RM kanálu a to znamená neposlat RM a vyvolání z čekající operace.</span><span class="sxs-lookup"><span data-stu-id="db94b-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="db94b-250">V opačném případě by měl být vrácená zpráva z Request() nebo Receive().</span><span class="sxs-lookup"><span data-stu-id="db94b-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="db94b-251">To zahrnuje případy, kdy vrstvě rozpozná chybu, ale chyby pouze označuje, že žádost se nezdařilo a neznamená přerušením kanálu a vyvolání z čekající operace.</span><span class="sxs-lookup"><span data-stu-id="db94b-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="db94b-252">Použitelnosti v takovém případě by měly implementovat vrstvě `GetProperty<FaultConverter>` a vraťte se `FaultConverter` odvozenou třídu, která můžete převést chyby výjimky tak, že přepíšete `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="db94b-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="db94b-253">Následující objektový model podporuje převod zprávy výjimky:</span><span class="sxs-lookup"><span data-stu-id="db94b-253">The following object model supports converting messages to exceptions:</span></span>  
  
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
  
 <span data-ttu-id="db94b-254">Kanál vrstvu můžete implementovat `GetProperty<FaultConverter>` pro podporu převodu chybové zprávy k výjimkám.</span><span class="sxs-lookup"><span data-stu-id="db94b-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="db94b-255">Uděláte to tak, přepsat `OnTryCreateException` a zkontrolujte chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="db94b-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="db94b-256">Je-li rozpoznán, provést převod, jinak požádejte vnitřního kanálu ho převést.</span><span class="sxs-lookup"><span data-stu-id="db94b-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="db94b-257">Přenosové kanály by měly delegovat do `FaultConverter.GetDefaultFaultConverter` aby se získal výchozí FaultConverter SOAP, WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="db94b-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="db94b-258">Obvyklá implementace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="db94b-258">A typical implementation looks like this:</span></span>  
  
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
  
 <span data-ttu-id="db94b-259">Pro konkrétní chyby podmínky, které mají odlišné obnovení scénáře, vezměte v úvahu definování odvozenou třídu `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="db94b-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="db94b-260">Zpracování MustUnderstand</span><span class="sxs-lookup"><span data-stu-id="db94b-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="db94b-261">SOAP definuje obecné chyby pro signalizaci, že požadovaná hlavička nebyla srozumitelné pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="db94b-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="db94b-262">Tato porucha se označuje jako `mustUnderstand` selhání.</span><span class="sxs-lookup"><span data-stu-id="db94b-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="db94b-263">Ve službě WCF, vlastních kanálů nikdy nevygeneruje `mustUnderstand` chyb.</span><span class="sxs-lookup"><span data-stu-id="db94b-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="db94b-264">Místo toho dispečer WCF, která se nachází v horní části zásobníku komunikace WCF, zkontroluje, který všechny hlavičky, které byly označeny jako MustUndestand = true byly srozumitelné pro základní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="db94b-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUndestand=true were understood by the underlying stack.</span></span> <span data-ttu-id="db94b-265">Pokud některý se nerozpoznaly, `mustUnderstand` selhání je vygenerována v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="db94b-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="db94b-266">(Uživatel může rozhodnout pro vypnutí to `mustUnderstand` zpracování a je aplikace přijímat všechny hlavičky zprávy.</span><span class="sxs-lookup"><span data-stu-id="db94b-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="db94b-267">In that Case aplikace zodpovídá za `mustUnderstand` zpracování.) Vygenerovaný selhání obsahuje hlavičku NotUnderstood, který obsahuje názvy všech záhlaví s MustUnderstand = true, který se nerozpoznaly.</span><span class="sxs-lookup"><span data-stu-id="db94b-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="db94b-268">Pokud váš kanál protokolu odesílá vlastní hlavičku s MustUnderstand = true a přijímá `mustUnderstand` selhání, se musí zjistit, zda je záhlaví je odeslat z důvodu tohoto selhání.</span><span class="sxs-lookup"><span data-stu-id="db94b-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="db94b-269">Existují dva členy na `MessageFault` třídu, která jsou užitečné pro toto:</span><span class="sxs-lookup"><span data-stu-id="db94b-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
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
  
 <span data-ttu-id="db94b-270">`IsMustUnderstandFault` Vrátí `true` Pokud se jedná `mustUnderstand` selhání.</span><span class="sxs-lookup"><span data-stu-id="db94b-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="db94b-271">`WasHeaderNotUnderstood` Vrátí `true` Pokud hlavička se zadaným názvem a oborem názvů je součástí selhání jako NotUnderstood záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db94b-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="db94b-272">V opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="db94b-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="db94b-273">Pokud kanál vysílá hlavičku, která je označena MustUnderstand = true, pak tuto vrstvu by měly také implementovat vzor rozhraní API pro generování výjimek a měli převést `mustUnderstand` chyby způsobené této hlavičky užitečnější výjimku, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="db94b-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="db94b-274">Trasování</span><span class="sxs-lookup"><span data-stu-id="db94b-274">Tracing</span></span>  
 <span data-ttu-id="db94b-275">Rozhraní .NET Framework poskytuje mechanismus pro trasování spuštění programu jako způsob, jak vám pomůže diagnostiku produkčních aplikací nebo přerušované problémy, kde není možné jenom připojení ladicího programu a krokovat kód.</span><span class="sxs-lookup"><span data-stu-id="db94b-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="db94b-276">Základní součásti tohoto mechanismu jsou v <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů a obsahovat:</span><span class="sxs-lookup"><span data-stu-id="db94b-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="db94b-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj informací trasování mají být zapsány, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, což je abstraktní základní třída pro konkrétní naslouchacích procesů, které zobrazí informace, které mají být vyvolány z <xref:System.Diagnostics.TraceSource> a vytvořit jeho výstup do cíle specifické pro naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="db94b-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="db94b-278">Například <xref:System.Diagnostics.XmlWriterTraceListener> výstupy trasovací informace do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="db94b-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="db94b-279">Nakonec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, která umožňuje řídit úroveň podrobností trasování uživatelů aplikace a je obvykle zadaný v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="db94b-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="db94b-280">Kromě základních komponent, můžete použít [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení a prohledávání WCF trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="db94b-281">Nástroj je určený speciálně pro trasovací soubory vygenerován pomocí WCF a zapsat pomocí <xref:System.Diagnostics.XmlWriterTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="db94b-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="db94b-282">Následující obrázek znázorňuje různé součásti účastnící se trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="db94b-283">![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="db94b-283">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="db94b-284">Trasování z vlastního kanálu</span><span class="sxs-lookup"><span data-stu-id="db94b-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="db94b-285">Vlastní kanály by měly vypsat zprávy trasování, které pomáhají při diagnostikování problémů, když není možné se připojit ladicí program k běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db94b-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="db94b-286">To zahrnuje dvě základní úlohy: Vytvoření instance <xref:System.Diagnostics.TraceSource> a volání metody zapsat trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="db94b-287">Při vytváření instance <xref:System.Diagnostics.TraceSource>, řetězec zadáte se stane název tohoto zdroje.</span><span class="sxs-lookup"><span data-stu-id="db94b-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="db94b-288">Tento název se používá ke konfiguraci (úroveň trasování povolit/zakázat/set) zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="db94b-289">Objevuje se taky ve výstupu samotné trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="db94b-290">Vlastní kanály používali název jedinečný zdroj k pomáhají čtenářům výstup trasování pochopit, odkud pochází informace o trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="db94b-291">Pomocí názvu sestavení, který zapisuje informace jako název zdroje trasování je běžný postup.</span><span class="sxs-lookup"><span data-stu-id="db94b-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="db94b-292">WCF například používá informace ze sestavení System.ServiceModel zapisovat System.ServiceModel jako zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="db94b-293">Jakmile budete mít zdroj trasování, můžete volat jeho <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metody zapsat trasování položky pro posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="db94b-294">Pro každou položku trasování zápisu, budete muset klasifikovat typ události jako jeden z typů událostí definovaných v <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="db94b-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="db94b-295">Tato klasifikace a nastavení úrovně trasování v konfiguraci zjistit, zda je položka sledování výstupu k naslouchacímu procesu.</span><span class="sxs-lookup"><span data-stu-id="db94b-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="db94b-296">Například v konfiguraci k nastavení úrovně trasování `Warning` umožňuje `Warning`, `Error` a `Critical` položky k zapsání ale bloky informace a podrobné záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="db94b-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="db94b-297">Tady je příklad vytvoření instance zdroje trasování a zápis položky na úrovni informace:</span><span class="sxs-lookup"><span data-stu-id="db94b-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="db94b-298">Důrazně doporučujeme, že zadáte název zdroje trasování, který je jedinečný pro váš vlastní kanál pomáhají čtenářům výstup trasování pochopit výstup, odkud.</span><span class="sxs-lookup"><span data-stu-id="db94b-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="db94b-299">Integrace s prohlížečem trasování</span><span class="sxs-lookup"><span data-stu-id="db94b-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="db94b-300">Trasování vygenerovaná kanálu může být výstup ve formátu, který dokáže přečíst [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pomocí <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="db94b-301">To není něco, jako vývojář kanálu, musíte udělat.</span><span class="sxs-lookup"><span data-stu-id="db94b-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="db94b-302">Místo toho je uživatel aplikace (nebo osoby, řešení potíží s aplikace), který by měl nakonfigurovat tento naslouchací proces trasování v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="db94b-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="db94b-303">Například následující konfigurace poskytuje trasovací informace z obou <xref:System.ServiceModel?displayProperty=nameWithType> a `Microsoft.Samples.Udp` do souboru s názvem `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="db94b-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="db94b-304">Trasování strukturovaných dat</span><span class="sxs-lookup"><span data-stu-id="db94b-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="db94b-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> má <xref:System.Diagnostics.TraceSource.TraceData%2A> metodu, která přebírá jeden nebo více objektů, které mají být zahrnuty v položce trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="db94b-306">Obecně platí <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda je volána na každý objekt a výsledný řetězec je zapsán jako součást položku trasování.</span><span class="sxs-lookup"><span data-stu-id="db94b-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="db94b-307">Při použití <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> do výstupu trasování, můžete předat <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako datový objekt k <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="db94b-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="db94b-308">Výsledný záznam trasování zahrnuje kód XML poskytnutý podle <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db94b-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="db94b-309">Tady je příklad položky s daty XML aplikace:</span><span class="sxs-lookup"><span data-stu-id="db94b-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="db94b-310">Prohlížeč trasování WCF rozumí schématu `TraceRecord` element uvedenému výše a extrahuje data z jeho podřízené prvky a zobrazí jej ve formátu tabulky.</span><span class="sxs-lookup"><span data-stu-id="db94b-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="db94b-311">Váš kanál používejte pro toto schéma aplikace strukturovaná data trasování, k poskytování pomoci uživatelům Svctraceviewer.exe číst data.</span><span class="sxs-lookup"><span data-stu-id="db94b-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
