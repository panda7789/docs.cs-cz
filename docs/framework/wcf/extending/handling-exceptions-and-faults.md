---
title: Zpracování výjimek a chyb
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 4f95907d4f88315f2815b84e2ceb4e069783438d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851276"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="ac496-102">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="ac496-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="ac496-103">Výjimky slouží ke sdělování chyb místně v rámci služby nebo implementace klienta.</span><span class="sxs-lookup"><span data-stu-id="ac496-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="ac496-104">Na druhé straně chyby slouží k sdělování chyb napříč hranicemi služby, například ze serveru do klienta nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="ac496-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="ac496-105">Kromě chyb využívají přenosové kanály často mechanismy přenosu pro komunikaci s chybami na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac496-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="ac496-106">Například přenos HTTP používá ke komunikaci neexistující adresy URL koncového bodu stavové kódy jako 404 (není k dispozici žádný koncový bod pro odeslání zpětné chyby).</span><span class="sxs-lookup"><span data-stu-id="ac496-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="ac496-107">Tento dokument se skládá ze tří částí, které poskytují pokyny pro vlastní autory kanálů.</span><span class="sxs-lookup"><span data-stu-id="ac496-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="ac496-108">První část poskytuje pokyny, kdy a jak definovat a vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="ac496-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="ac496-109">Druhá část obsahuje pokyny k vytváření a využívání chyb.</span><span class="sxs-lookup"><span data-stu-id="ac496-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="ac496-110">Třetí část vysvětluje, jak poskytnout trasovací informace pro pomoc uživateli vlastního kanálu při odstraňování potíží se spuštěnými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="ac496-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="ac496-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="ac496-111">Exceptions</span></span>  
 <span data-ttu-id="ac496-112">Při vyvolání výjimky je třeba mít na paměti dvě věci: Nejprve musí být typ, který umožňuje uživatelům napsat správný kód, který může reagovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="ac496-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="ac496-113">Za druhé musí poskytnout dostatek informací, aby mohl uživatel pochopit, co se nepovedlo, dopad na selhání a jak ho opravit.</span><span class="sxs-lookup"><span data-stu-id="ac496-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="ac496-114">Následující části obsahují pokyny týkající se typů výjimek a zpráv pro kanály Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ac496-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="ac496-115">V pokynech pro návrh dokumentu výjimek jsou také k dispozici obecné pokyny týkající se výjimek v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ac496-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="ac496-116">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="ac496-116">Exception Types</span></span>  
 <span data-ttu-id="ac496-117">Všechny výjimky vyvolané kanály musí být buď <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>nebo typu odvozeného z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="ac496-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="ac496-118">(Například <xref:System.ObjectDisposedException> může být vyvolána výjimka, ale pouze pro indikaci, že volající kód má nepoužitý kanál.</span><span class="sxs-lookup"><span data-stu-id="ac496-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="ac496-119">Pokud se kanál používá správně, musí vyvolávat pouze dané výjimky.) Služba WCF poskytuje sedm typů výjimek, které <xref:System.ServiceModel.CommunicationException> jsou odvozeny z a jsou navrženy pro použití v kanálech.</span><span class="sxs-lookup"><span data-stu-id="ac496-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="ac496-120">Existují jiné <xref:System.ServiceModel.CommunicationException>odvozené výjimky, které jsou určeny pro použití jinými částmi systému.</span><span class="sxs-lookup"><span data-stu-id="ac496-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="ac496-121">Tyto typy výjimek jsou:</span><span class="sxs-lookup"><span data-stu-id="ac496-121">These exception types are:</span></span>  
  
|<span data-ttu-id="ac496-122">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="ac496-122">Exception Type</span></span>|<span data-ttu-id="ac496-123">Význam</span><span class="sxs-lookup"><span data-stu-id="ac496-123">Meaning</span></span>|<span data-ttu-id="ac496-124">Obsah vnitřní výjimky</span><span class="sxs-lookup"><span data-stu-id="ac496-124">Inner Exception Content</span></span>|<span data-ttu-id="ac496-125">Strategie obnovení</span><span class="sxs-lookup"><span data-stu-id="ac496-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="ac496-126">Adresa koncového bodu určená pro naslouchání se již používá.</span><span class="sxs-lookup"><span data-stu-id="ac496-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="ac496-127">Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="ac496-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="ac496-128">Například.</span><span class="sxs-lookup"><span data-stu-id="ac496-128">For example.</span></span> <span data-ttu-id="ac496-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>nebo .<xref:System.Net.Sockets.SocketException></span><span class="sxs-lookup"><span data-stu-id="ac496-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="ac496-130">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="ac496-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="ac496-131">Proces není povolený přístup k adrese koncového bodu zadané pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="ac496-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="ac496-132">Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="ac496-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="ac496-133">Například <xref:System.IO.PipeException>, nebo <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="ac496-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="ac496-134">Zkuste použít jiné přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="ac496-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="ac496-135">Používané je v chybovém stavu (Další informace najdete v tématu [porozumění změnám stavu](understanding-state-changes.md)). <xref:System.ServiceModel.ICommunicationObject></span><span class="sxs-lookup"><span data-stu-id="ac496-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="ac496-136">Všimněte si, že pokud objekt s více nevyřízenými voláními přechází do chybového stavu, vyvolá pouze jedno volání výjimku, která souvisí s chybou a zbytek volání vyvolá <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="ac496-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="ac496-137">Tato výjimka je obvykle vyvolána, protože aplikace vyhledává určitou výjimku a pokouší se použít již chybný objekt, pravděpodobně na jiném vlákně, než je ten, který zachytil původní výjimku.</span><span class="sxs-lookup"><span data-stu-id="ac496-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="ac496-138">Pokud je k dispozici, zobrazí se podrobnosti o vnitřní výjimce.</span><span class="sxs-lookup"><span data-stu-id="ac496-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="ac496-139">Vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="ac496-139">Create a new object.</span></span> <span data-ttu-id="ac496-140">Všimněte si, že v závislosti na tom <xref:System.ServiceModel.ICommunicationObject> , co způsobilo chybu v prvním místě, může být nutné provést i další práci.</span><span class="sxs-lookup"><span data-stu-id="ac496-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="ac496-141">Použití se přerušilo (Další informace najdete v tématu [porozumění změnám stavu](understanding-state-changes.md)). <xref:System.ServiceModel.ICommunicationObject></span><span class="sxs-lookup"><span data-stu-id="ac496-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="ac496-142">Podobně jako <xref:System.ServiceModel.ICommunicationObject.Abort%2A> , jeho výjimka označuje, že aplikace volala na objektu, případně z jiného vlákna, a objekt již z tohoto důvodu není použitelný. <xref:System.ServiceModel.CommunicationObjectFaultedException></span><span class="sxs-lookup"><span data-stu-id="ac496-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="ac496-143">Pokud je k dispozici, zobrazí se podrobnosti o vnitřní výjimce.</span><span class="sxs-lookup"><span data-stu-id="ac496-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="ac496-144">Vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="ac496-144">Create a new object.</span></span> <span data-ttu-id="ac496-145">Všimněte si, že v závislosti na tom <xref:System.ServiceModel.ICommunicationObject> , co způsobilo přerušení v prvním místě, může být nutné provést i další práci.</span><span class="sxs-lookup"><span data-stu-id="ac496-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="ac496-146">Cílový vzdálený koncový bod nenaslouchá.</span><span class="sxs-lookup"><span data-stu-id="ac496-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="ac496-147">To může vést k tomu, že všechny části adresy koncového bodu jsou nesprávné, nevyřešitelná nebo koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ac496-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="ac496-148">Mezi příklady patří Chyba služby DNS, správce front není dostupný a služba není spuštěná.</span><span class="sxs-lookup"><span data-stu-id="ac496-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="ac496-149">Vnitřní výjimka poskytuje podrobnosti, obvykle z podkladového přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac496-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="ac496-150">Zkuste jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="ac496-150">Try a different address.</span></span> <span data-ttu-id="ac496-151">Případně může odesílatel chvíli počkat a zkusit to znovu, pokud služba byla vypnutá.</span><span class="sxs-lookup"><span data-stu-id="ac496-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="ac496-152">Komunikační protokoly, jak je popsáno v zásadách koncového bodu, se neshodují mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="ac496-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="ac496-153">Například byl překročen počet neshody typů obsahu rámců nebo maximální velikost zprávy.</span><span class="sxs-lookup"><span data-stu-id="ac496-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="ac496-154">Pokud je k dispozici, zobrazí se další informace o chybě konkrétního protokolu.</span><span class="sxs-lookup"><span data-stu-id="ac496-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="ac496-155">Například je vnitřní <xref:System.ServiceModel.QuotaExceededException> výjimka, když příčina chyby překročí třídu MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="ac496-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="ac496-156">Pohledávky Ujistěte se, že odesílatel a přijatý nastavení protokolu odpovídají.</span><span class="sxs-lookup"><span data-stu-id="ac496-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="ac496-157">To lze provést tak, že znovu naimportujete metadata koncového bodu služby (zásady) a pomocí vygenerované vazby znovu vytvoříte kanál.</span><span class="sxs-lookup"><span data-stu-id="ac496-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="ac496-158">Vzdálený koncový bod naslouchá, ale není připraven ke zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="ac496-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="ac496-159">Je-li k dispozici, vnitřní výjimka poskytuje chyby protokolu SOAP nebo podrobnosti o chybě na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="ac496-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="ac496-160">Pohledávky Počkejte a opakujte operaci později.</span><span class="sxs-lookup"><span data-stu-id="ac496-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="ac496-161">Operaci se nepovedlo dokončit v časovém limitu.</span><span class="sxs-lookup"><span data-stu-id="ac496-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="ac496-162">Může poskytnout podrobnosti o vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="ac496-162">May provide details about the timeout.</span></span>|<span data-ttu-id="ac496-163">Počkejte a opakujte operaci později.</span><span class="sxs-lookup"><span data-stu-id="ac496-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="ac496-164">Definujte nový typ výjimky pouze v případě, že tento typ odpovídá konkrétní strategii obnovení, která se liší od všech stávajících typů výjimek.</span><span class="sxs-lookup"><span data-stu-id="ac496-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="ac496-165">Pokud definujete nový typ výjimky, musí odvozovat z <xref:System.ServiceModel.CommunicationException> nebo jedné z jeho odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="ac496-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="ac496-166">Zprávy výjimek</span><span class="sxs-lookup"><span data-stu-id="ac496-166">Exception Messages</span></span>  
 <span data-ttu-id="ac496-167">Zprávy o výjimkách jsou zaměřeny na uživatele, který není programem, takže by měli poskytnout dostatečné informace, které uživateli pomohou pochopit a vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="ac496-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="ac496-168">Mezi tři podstatné části dobré zprávy o výjimce patří:</span><span class="sxs-lookup"><span data-stu-id="ac496-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="ac496-169">Co se přihodilo.</span><span class="sxs-lookup"><span data-stu-id="ac496-169">What happened.</span></span> <span data-ttu-id="ac496-170">Zadejte jasný popis problému s použitím podmínek, které se vztahují k uživatelskému prostředí.</span><span class="sxs-lookup"><span data-stu-id="ac496-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="ac496-171">Zpráva o špatné výjimce by mohla být například "neplatný konfigurační oddíl".</span><span class="sxs-lookup"><span data-stu-id="ac496-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="ac496-172">Tím se uživateli zajímá, který konfigurační oddíl je nesprávný a proč není správný.</span><span class="sxs-lookup"><span data-stu-id="ac496-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="ac496-173">Vylepšená zpráva bude "neplatný konfigurační oddíl \<CustomBinding >".</span><span class="sxs-lookup"><span data-stu-id="ac496-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="ac496-174">Ještě lepší zpráva by byla "nelze přidat Transport s názvem myTransport do vazby s názvem myBinding, protože vazba již má Transport s názvem myTransport".</span><span class="sxs-lookup"><span data-stu-id="ac496-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="ac496-175">Toto je velmi specifická zpráva s použitím podmínek a názvů, které může uživatel snadno identifikovat v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ac496-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="ac496-176">Stále však chybí několik klíčových součástí.</span><span class="sxs-lookup"><span data-stu-id="ac496-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="ac496-177">Význam chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-177">The significance of the error.</span></span> <span data-ttu-id="ac496-178">Pokud se zpráva nezřetelně nejedná o chybu, uživatel bude pravděpodobně zajímat, zda se jedná o závažnou chybu, nebo zda může být ignorována.</span><span class="sxs-lookup"><span data-stu-id="ac496-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="ac496-179">Obecně by zprávy měly vést s významem nebo významem chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="ac496-180">Chcete-li zlepšit předchozí příklad, zpráva mohla být "hostitel ServiceHost se nepodařilo otevřít z důvodu chyby v konfiguraci: Do vazby s názvem myBinding nelze přidat Transport s názvem myTransport, protože vazba již má Transport s názvem myTransport.</span><span class="sxs-lookup"><span data-stu-id="ac496-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="ac496-181">Jak by měl uživatel problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="ac496-181">How the user should correct the problem.</span></span> <span data-ttu-id="ac496-182">Nejdůležitější část zprávy pomáhá uživateli problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="ac496-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="ac496-183">Zpráva by měla obsahovat některé doprovodné materiály nebo doporučení týkající se toho, co je třeba opravit nebo opravit, aby problém mohl vyřešit.</span><span class="sxs-lookup"><span data-stu-id="ac496-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="ac496-184">Například "hostitel ServiceHost se nepodařilo otevřít z důvodu chyby v konfiguraci: Do vazby s názvem myBinding nelze přidat Transport s názvem myTransport, protože vazba již má Transport s názvem myTransport.</span><span class="sxs-lookup"><span data-stu-id="ac496-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="ac496-185">Ujistěte se prosím, že vazba obsahuje jenom jeden přenos.</span><span class="sxs-lookup"><span data-stu-id="ac496-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="ac496-186">Komunikace s chybami</span><span class="sxs-lookup"><span data-stu-id="ac496-186">Communicating Faults</span></span>  
 <span data-ttu-id="ac496-187">SOAP 1,1 a SOAP 1,2 definují specifickou strukturu pro chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="ac496-188">Existují některé rozdíly mezi těmito dvěma specifikacemi, ale obecně jsou typy zpráva a parametr MessageFault použity k vytváření a zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="ac496-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="ac496-189">![Zpracování výjimek a chyb](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="ac496-189">![Handling exceptions and faults](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="ac496-190">Chyba protokolu SOAP 1,2 (Left) a chyby SOAP 1,1 (vpravo).</span><span class="sxs-lookup"><span data-stu-id="ac496-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="ac496-191">Všimněte si, že v SOAP 1,1 pouze element fault je kvalifikovaný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ac496-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="ac496-192">SOAP definuje zprávu o chybě jako zprávu, která obsahuje pouze element Fault (element, jehož název je `<env:Fault>`) jako `<env:Body>`podřízený objekt.</span><span class="sxs-lookup"><span data-stu-id="ac496-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="ac496-193">Obsah chybného prvku se mírně liší mezi SOAP 1,1 a SOAP 1,2, jak je znázorněno na obrázku 1.</span><span class="sxs-lookup"><span data-stu-id="ac496-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="ac496-194"><xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> Nicméně třída normalizuje tyto rozdíly do jednoho objektového modelu:</span><span class="sxs-lookup"><span data-stu-id="ac496-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
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
  
 <span data-ttu-id="ac496-195">Vlastnost odpovídá `env:Code` ( nebo`faultCode` v SOAP 1,1) a identifikuje typ chyby. `Code`</span><span class="sxs-lookup"><span data-stu-id="ac496-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="ac496-196">Protokol SOAP 1,2 definuje pět přípustných hodnot `faultCode` pro (například sender a přijímač) a `Subcode` definuje element, který může obsahovat libovolnou hodnotu podkódu.</span><span class="sxs-lookup"><span data-stu-id="ac496-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="ac496-197">(Viz [specifikace protokolu SOAP 1,2](https://go.microsoft.com/fwlink/?LinkId=95176) pro seznam povolených kódů chyb a jejich význam) Protokol SOAP 1,1 má mírně odlišný mechanismus: Definuje čtyři `faultCode` hodnoty (například klient a Server), které se dají rozšířit tak, že se nadefinují zcela nové nebo pomocí zápisu teček vytvoří `faultCodes`konkrétnější, například Client. Authentication.</span><span class="sxs-lookup"><span data-stu-id="ac496-197">(See the [SOAP 1.2 specification](https://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="ac496-198">Použijete-li parametr MessageFault k programovým chybám, FaultCode.Name a FaultCode. Namespace se mapují na název a obor názvů protokolu SOAP `env:Code` 1,2 nebo SOAP 1,1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="ac496-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="ac496-199">FaultCode. Subcode mapuje na `env:Subcode` pro SOAP 1,2 a má hodnotu null pro SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="ac496-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="ac496-200">Měli byste vytvořit nové podkódy chyb (nebo nové kódy chyb, pokud používáte protokol SOAP 1,1), pokud je to zajímavé pro programové odlišení chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="ac496-201">To je podobné jako vytvoření nového typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="ac496-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="ac496-202">Nepoužívejte zápis tečky s kódy chyb SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="ac496-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="ac496-203">( [Základní profil WS-I](https://go.microsoft.com/fwlink/?LinkId=95177) také nedoporučuje použití zápisu teček v kódu chyby.)</span><span class="sxs-lookup"><span data-stu-id="ac496-203">(The [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
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
  
 <span data-ttu-id="ac496-204">Vlastnost odpovídá `env:Reason` ( nebo`faultString` v SOAP 1,1) Popis chybového stavu, který se podobá zprávě výjimky, uživatelsky čitelný. `Reason`</span><span class="sxs-lookup"><span data-stu-id="ac496-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="ac496-205">Třída (a SOAP `env:Reason/faultString`) obsahuje integrovanou podporu pro více překladů v zájmu globalizace. `FaultReason`</span><span class="sxs-lookup"><span data-stu-id="ac496-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
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
  
 <span data-ttu-id="ac496-206">Obsah podrobností o chybě se zveřejňuje na parametr MessageFault pomocí různých metod, `GetDetail`včetně \<T > `GetReaderAtDetailContents`a ().</span><span class="sxs-lookup"><span data-stu-id="ac496-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="ac496-207">Podrobnosti o chybě je neprůhledný prvek pro další podrobnosti o chybě.</span><span class="sxs-lookup"><span data-stu-id="ac496-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="ac496-208">To je užitečné v případě, že existuje několik libovolných strukturovaných podrobností, které chcete s chybou přenášet.</span><span class="sxs-lookup"><span data-stu-id="ac496-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="ac496-209">Generují se chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-209">Generating Faults</span></span>  
 <span data-ttu-id="ac496-210">Tato část vysvětluje proces generování chyby v reakci na chybový stav zjištěný v kanálu nebo ve vlastnosti zprávy vytvořené kanálem.</span><span class="sxs-lookup"><span data-stu-id="ac496-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="ac496-211">Typický příklad posílá zpět chybu v reakci na zprávu požadavku, která obsahuje neplatná data.</span><span class="sxs-lookup"><span data-stu-id="ac496-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="ac496-212">Při generování chyby by vlastní kanál neměl přímo odeslat chybu, místo toho by měla vyvolat výjimku a nechat vrstvu výše rozhodnout, zda má být tato výjimka převedena na chybu a jak ji odeslat.</span><span class="sxs-lookup"><span data-stu-id="ac496-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="ac496-213">Pro pomoc v tomto převodu by měl kanál poskytnout `FaultConverter` implementaci, která může převést výjimku vyvolanou vlastním kanálem na příslušnou chybu.</span><span class="sxs-lookup"><span data-stu-id="ac496-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="ac496-214">`FaultConverter`je definován jako:</span><span class="sxs-lookup"><span data-stu-id="ac496-214">`FaultConverter` is defined as:</span></span>  
  
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
  
 <span data-ttu-id="ac496-215">Každý kanál, který generuje vlastní chyby, musí `FaultConverter` implementovat a vrátit ho z `GetProperty<FaultConverter>`volání.</span><span class="sxs-lookup"><span data-stu-id="ac496-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="ac496-216">Vlastní `OnTryCreateFaultMessage` implementace musí buď převést výjimku na chybu, nebo delegovat na vnitřní `FaultConverter`kanál.</span><span class="sxs-lookup"><span data-stu-id="ac496-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="ac496-217">Pokud je kanálem přenos, musí buď převést výjimku nebo delegáta na kodér `FaultConverter` nebo na výchozí hodnotu `FaultConverter` poskytnutou v rámci WCF.</span><span class="sxs-lookup"><span data-stu-id="ac496-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="ac496-218">Výchozí hodnota `FaultConverter` převádí chyby odpovídající chybovým zprávám určeným protokolem WS-Addressing a SOAP.</span><span class="sxs-lookup"><span data-stu-id="ac496-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="ac496-219">Tady je příklad `OnTryCreateFaultMessage` implementace.</span><span class="sxs-lookup"><span data-stu-id="ac496-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
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
  
 <span data-ttu-id="ac496-220">Nenásobení tohoto vzoru je, že výjimky vyvolané mezi vrstvami pro chybové stavy, které vyžadují chyby, musí obsahovat dostatek informací pro odpovídající generátor chyb pro vytvoření správné chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="ac496-221">Jako autor vlastního kanálu můžete definovat typy výjimek, které odpovídají různým chybám, pokud takové výjimky ještě neexistují.</span><span class="sxs-lookup"><span data-stu-id="ac496-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="ac496-222">Všimněte si, že vrstvy přesměrované kanály by měly sdělit chybový stav, nikoli neprůhledná data chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="ac496-223">Kategorie chyb</span><span class="sxs-lookup"><span data-stu-id="ac496-223">Fault Categories</span></span>  
 <span data-ttu-id="ac496-224">Existují všeobecně tři kategorie chyb:</span><span class="sxs-lookup"><span data-stu-id="ac496-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="ac496-225">Chyby, které se Pervasive v celém zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ac496-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="ac496-226">K těmto chybám může dojít v libovolné vrstvě v zásobníku kanálů, například InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="ac496-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="ac496-227">Chyby, které mohou být zjištěny kdekoli nad určitou vrstvou v zásobníku, například některé chyby, které se týkají toku transakce nebo rolí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ac496-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="ac496-228">Chyby směrované na jednu vrstvu v zásobníku, například chyby, jako je číslo sekvence WS-RM, chyba.</span><span class="sxs-lookup"><span data-stu-id="ac496-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="ac496-229">Kategorie 1.</span><span class="sxs-lookup"><span data-stu-id="ac496-229">Category 1.</span></span> <span data-ttu-id="ac496-230">Chyby jsou obecně WS-Addressing a SOAP chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="ac496-231">Základní `FaultConverter` třída poskytovaná službou WCF převádí chyby odpovídající chybovým zprávám určeným protokolem WS-Addressing a SOAP, takže nemusíte sami zpracovávat převod těchto výjimek.</span><span class="sxs-lookup"><span data-stu-id="ac496-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="ac496-232">Kategorie 2.</span><span class="sxs-lookup"><span data-stu-id="ac496-232">Category 2.</span></span> <span data-ttu-id="ac496-233">K chybám dochází, když vrstva přidá vlastnost do zprávy, která zcela nespotřebovává informace zprávy, které se vztahují k této vrstvě.</span><span class="sxs-lookup"><span data-stu-id="ac496-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="ac496-234">Chyby mohou být zjištěny později, pokud vyšší vrstva požádá o vlastnost zprávy o zpracování informací o zprávách.</span><span class="sxs-lookup"><span data-stu-id="ac496-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="ac496-235">Tyto kanály by měly implementovat `GetProperty` výše zadanou metodu, aby bylo možné zvýšit úroveň, aby bylo možné znovu odeslat správnou chybu.</span><span class="sxs-lookup"><span data-stu-id="ac496-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="ac496-236">Příkladem je TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="ac496-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="ac496-237">Tato vlastnost se přidá do zprávy bez úplného ověřování všech dat v hlavičce (v takovém případě může zahrnovat kontaktování služby DTC (Distributed Transaction Coordinator).</span><span class="sxs-lookup"><span data-stu-id="ac496-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="ac496-238">Kategorie 3.</span><span class="sxs-lookup"><span data-stu-id="ac496-238">Category 3.</span></span> <span data-ttu-id="ac496-239">Chyby jsou generovány a odesílány pouze jednou vrstvou v procesoru.</span><span class="sxs-lookup"><span data-stu-id="ac496-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="ac496-240">Všechny výjimky jsou proto obsaženy v rámci vrstvy.</span><span class="sxs-lookup"><span data-stu-id="ac496-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="ac496-241">Aby bylo možné zvýšit konzistenci mezi kanály a snadnou údržbou, váš vlastní kanál by měl pomocí výše uvedeného vzoru vygenerovat chybové zprávy, a to i u interních chyb.</span><span class="sxs-lookup"><span data-stu-id="ac496-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="ac496-242">Interpretují se přijaté chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="ac496-243">V této části najdete pokyny k vygenerování vhodné výjimky při příjmu chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="ac496-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="ac496-244">Rozhodovací strom pro zpracování zprávy v každé vrstvě v zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="ac496-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="ac496-245">Pokud vrstva považuje zprávu za neplatnou, měla by tato vrstva provádět zpracování "neplatné zprávy".</span><span class="sxs-lookup"><span data-stu-id="ac496-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="ac496-246">Toto zpracování je specifické pro vrstvu, ale může zahrnovat vyřazení zprávy, trasování nebo vyvolání výjimky, která je převedena na chybu.</span><span class="sxs-lookup"><span data-stu-id="ac496-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="ac496-247">Příkladem může být zabezpečení přijímání zprávy, která není správně zabezpečena nebo správce prostředků obdržel zprávu s chybným pořadovým číslem.</span><span class="sxs-lookup"><span data-stu-id="ac496-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="ac496-248">V opačném případě, pokud se jedná o zprávu o chybě, která se vztahuje konkrétně na vrstvu, a zpráva není smysluplná mimo interakci vrstvy, měla by vrstva zpracovat chybový stav.</span><span class="sxs-lookup"><span data-stu-id="ac496-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="ac496-249">Příkladem je, že sekvence RM odmítla chybu, která nemá smysl na vrstvy nad kanálem RM a který implikuje chybu kanálu RM a vyvolává se z nevyřízených operací.</span><span class="sxs-lookup"><span data-stu-id="ac496-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="ac496-250">V opačném případě by měla být zpráva vrácena z Request () nebo Receive ().</span><span class="sxs-lookup"><span data-stu-id="ac496-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="ac496-251">To zahrnuje případy, kdy vrstva rozpoznala chybu, ale chyba právě indikuje, že žádost selhala a neznamená chybu kanálu a vyvolání z nevyřízených operací.</span><span class="sxs-lookup"><span data-stu-id="ac496-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="ac496-252">Pro zlepšení použitelnosti v takovém případě by měla vrstva implementovat `GetProperty<FaultConverter>` a `FaultConverter` vracet odvozenou třídu, která může převést chybu na výjimku přepsáním `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="ac496-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="ac496-253">Následující objektový model podporuje převod zpráv na výjimky:</span><span class="sxs-lookup"><span data-stu-id="ac496-253">The following object model supports converting messages to exceptions:</span></span>  
  
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
  
 <span data-ttu-id="ac496-254">Vrstvu kanálu lze implementovat `GetProperty<FaultConverter>` pro podporu převodu chybových zpráv na výjimky.</span><span class="sxs-lookup"><span data-stu-id="ac496-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="ac496-255">Provedete to tak `OnTryCreateException` , že přepíšete a zkontrolujete zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="ac496-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="ac496-256">Je-li rozpoznán, proveďte převod, jinak požádejte o převod na vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="ac496-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="ac496-257">Přenosové kanály by měly `FaultConverter.GetDefaultFaultConverter` delegovat na, aby se získal výchozí protokol SOAP/WS-Addressing FaultConverter.</span><span class="sxs-lookup"><span data-stu-id="ac496-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="ac496-258">Typická implementace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="ac496-258">A typical implementation looks like this:</span></span>  
  
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
  
 <span data-ttu-id="ac496-259">Pro konkrétní chybové stavy, které mají odlišné scénáře obnovení, zvažte definování odvozené třídy `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="ac496-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="ac496-260">Zpracování MustUnderstand</span><span class="sxs-lookup"><span data-stu-id="ac496-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="ac496-261">Protokol SOAP definuje obecnou chybu pro signalizaci, že příjemce nerozuměl požadované záhlaví.</span><span class="sxs-lookup"><span data-stu-id="ac496-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="ac496-262">Tato chyba se označuje jako `mustUnderstand` chyba.</span><span class="sxs-lookup"><span data-stu-id="ac496-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="ac496-263">V WCF vlastní kanály nikdy negenerují `mustUnderstand` chyby.</span><span class="sxs-lookup"><span data-stu-id="ac496-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="ac496-264">Místo toho služba WCF Dispatcher, která je umístěna v horní části komunikačního zásobníku WCF, zkontroluje, zda je v podkladovém zásobníku porozuměla všechna záhlaví označená jako MustUnderstand = true.</span><span class="sxs-lookup"><span data-stu-id="ac496-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="ac496-265">Pokud některý z `mustUnderstand` nich nebyl srozumitelný, v tomto okamžiku je vygenerována chyba.</span><span class="sxs-lookup"><span data-stu-id="ac496-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="ac496-266">(Uživatel se může rozhodnout toto `mustUnderstand` zpracování vypnout a aplikace obdrží všechna záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="ac496-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="ac496-267">V takovém případě je aplikace zodpovědná za provádění `mustUnderstand` zpracování.) Vygenerovaná chyba zahrnuje hlavičku NotUnderstood, která obsahuje názvy všech hlaviček s MustUnderstand = true, které se nerozuměly.</span><span class="sxs-lookup"><span data-stu-id="ac496-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="ac496-268">Pokud kanál protokolu odešle vlastní hlavičku s MustUnderstand = true a dostane `mustUnderstand` chybu, musí zjistit, jestli je tato chyba způsobená hlavičkou, kterou odeslala.</span><span class="sxs-lookup"><span data-stu-id="ac496-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="ac496-269">Existují dva členy `MessageFault` třídy, které jsou užitečné pro tuto třídu:</span><span class="sxs-lookup"><span data-stu-id="ac496-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
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
  
 <span data-ttu-id="ac496-270">`IsMustUnderstandFault`Vrátí `true` , zda se jedná o `mustUnderstand` chybu.</span><span class="sxs-lookup"><span data-stu-id="ac496-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="ac496-271">`WasHeaderNotUnderstood`Vrátí `true` , zda je hlavička se zadaným názvem a oborem názvů zahrnuta do chyby jako NotUnderstood hlavička.</span><span class="sxs-lookup"><span data-stu-id="ac496-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="ac496-272">V opačném případě `false`vrátí.</span><span class="sxs-lookup"><span data-stu-id="ac496-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="ac496-273">Pokud kanál vygeneruje hlavičku, která je označena jako MustUnderstand = true, pak by tato vrstva měla také implementovat vzor rozhraní API generování výjimek a `mustUnderstand` měla by převést chyby způsobené touto hlavičkou na užitečnější výjimku, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="ac496-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="ac496-274">Trasování</span><span class="sxs-lookup"><span data-stu-id="ac496-274">Tracing</span></span>  
 <span data-ttu-id="ac496-275">.NET Framework poskytuje mechanismus pro trasování spuštění programu jako způsob, jak pomoci diagnostikovat produkčních aplikací nebo občasné problémy, kde není možné pouze připojit ladicí program a krokovat kód.</span><span class="sxs-lookup"><span data-stu-id="ac496-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="ac496-276">Základní komponenty tohoto mechanismu jsou v <xref:System.Diagnostics?displayProperty=nameWithType> oboru názvů a sestávají z:</span><span class="sxs-lookup"><span data-stu-id="ac496-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="ac496-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj trasovacích informací, které mají být zapsány, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>což je abstraktní základní třída pro konkrétní naslouchací procesy, které obdrží informace, které mají být trasovány z rozhraní <xref:System.Diagnostics.TraceSource> a jejich výstup do cíle specifického pro naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="ac496-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="ac496-278">Například <xref:System.Diagnostics.XmlWriterTraceListener> výstup trasovacích informací do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="ac496-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="ac496-279"><xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>Nakonec, který umožňuje uživateli aplikace řídit podrobnosti trasování a je obvykle určen v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ac496-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="ac496-280">Kromě základních komponent můžete použít [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení a hledání trasování WCF.</span><span class="sxs-lookup"><span data-stu-id="ac496-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="ac496-281">Nástroj je navržen speciálně pro trasovací soubory generované službou WCF a zapisují pomocí <xref:System.Diagnostics.XmlWriterTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="ac496-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="ac496-282">Následující obrázek znázorňuje různé komponenty, které jsou součástí trasování.</span><span class="sxs-lookup"><span data-stu-id="ac496-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="ac496-283">![Zpracování výjimek a chyb](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="ac496-283">![Handling exceptions and faults](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="ac496-284">Trasování z vlastního kanálu</span><span class="sxs-lookup"><span data-stu-id="ac496-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="ac496-285">Vlastní kanály by měly vypsat zprávy trasování, které vám pomůžou diagnostikovat problémy, když není možné připojit ladicí program ke spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ac496-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="ac496-286">To zahrnuje dva úlohy na vysoké úrovni: Vytvoření instance a volání jejích metod pro zápis trasování. <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ac496-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="ac496-287">Při instanciování <xref:System.Diagnostics.TraceSource>se řetězec, který zadáte, bude název tohoto zdroje.</span><span class="sxs-lookup"><span data-stu-id="ac496-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="ac496-288">Tento název se používá ke konfiguraci (povolení nebo zakázání/nastavení úrovně trasování) zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="ac496-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="ac496-289">Také se zobrazí ve výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="ac496-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="ac496-290">Vlastní kanály by měly používat jedinečný název zdroje, aby usnadnili čtenářům výstup trasování pochopit, odkud informace o trasování pocházejí.</span><span class="sxs-lookup"><span data-stu-id="ac496-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="ac496-291">Použití názvu sestavení, které zapisuje informace jako název zdroje trasování, je běžný postup.</span><span class="sxs-lookup"><span data-stu-id="ac496-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="ac496-292">Například WCF používá jako zdroj trasování System. ServiceModel pro informace napsané ze sestavení System. ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="ac496-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="ac496-293">Jakmile budete mít zdroj trasování, zavoláte jeho <xref:System.Diagnostics.TraceSource.TraceData%2A>metody <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> pro zápis trasovacích položek do posluchačů trasování.</span><span class="sxs-lookup"><span data-stu-id="ac496-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="ac496-294">Pro každý záznam trasování, který zapíšete, je třeba klasifikovat typ události jako jeden z typů události definovaných v <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="ac496-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="ac496-295">Tato klasifikace a nastavení úrovně trasování v konfiguraci určují, zda je záznam trasování výstupem naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="ac496-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="ac496-296">Například nastavení úrovně trasování v konfiguraci tak, `Warning` aby umožňovalo `Warning`zápis položek, které mají být zapsány, `Error` `Critical` ale zablokují informace a podrobné položky.</span><span class="sxs-lookup"><span data-stu-id="ac496-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="ac496-297">Tady je příklad vytvoření instance zdroje trasování a zápis položky na úrovni informací:</span><span class="sxs-lookup"><span data-stu-id="ac496-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="ac496-298">Důrazně doporučujeme zadat název zdroje trasování, který je jedinečný pro váš vlastní kanál, aby bylo možné sledovat čtecí zařízení pro výstup a pochopit, odkud výstup pochází.</span><span class="sxs-lookup"><span data-stu-id="ac496-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="ac496-299">Integrace s prohlížečem trasování</span><span class="sxs-lookup"><span data-stu-id="ac496-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="ac496-300">Trasování generovaná vaším kanálem může být výstupem ve formátu čitelném [nástrojem Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) , a to <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> pomocí naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="ac496-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="ac496-301">Nejedná se o něco, co je třeba pro vývojáře kanálu.</span><span class="sxs-lookup"><span data-stu-id="ac496-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="ac496-302">Místo toho je uživatel aplikace (nebo osoba, která řešení potíží s aplikací), která vyžaduje konfiguraci tohoto naslouchacího procesu trasování v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ac496-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="ac496-303">Následující konfigurace například výstup trasovacích informací z obou <xref:System.ServiceModel?displayProperty=nameWithType> a `Microsoft.Samples.Udp` do souboru s názvem `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="ac496-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="ac496-304">Trasování strukturovaných dat</span><span class="sxs-lookup"><span data-stu-id="ac496-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="ac496-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType><xref:System.Diagnostics.TraceSource.TraceData%2A> má metodu, která přebírá jeden nebo více objektů, které mají být zahrnuty do položky trasování.</span><span class="sxs-lookup"><span data-stu-id="ac496-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="ac496-306">Obecně <xref:System.Object.ToString%2A?displayProperty=nameWithType> je metoda volána pro každý objekt a výsledný řetězec je zapsán jako součást položky trasování.</span><span class="sxs-lookup"><span data-stu-id="ac496-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="ac496-307">Při použití <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> pro výstup trasování můžete <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> předat jako datový objekt do <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac496-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="ac496-308">Výsledná položka trasování obsahuje XML, které poskytuje <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac496-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac496-309">Tady je příklad položky s daty aplikace XML:</span><span class="sxs-lookup"><span data-stu-id="ac496-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="ac496-310">Prohlížeč trasování WCF rozumí schématu `TraceRecord` dříve zobrazeného prvku a extrahuje data z jejích podřízených prvků a zobrazí je v tabulkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="ac496-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="ac496-311">Kanál by měl používat toto schéma při trasování strukturovaných dat aplikace, aby uživatelé SvcTraceViewer. exe mohli data číst.</span><span class="sxs-lookup"><span data-stu-id="ac496-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
