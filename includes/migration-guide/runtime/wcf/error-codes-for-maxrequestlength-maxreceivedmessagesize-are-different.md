---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620053"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="f7926-101">Kódy chyb pro maxRequestLength nebo třídu maxReceivedMessageSize se liší.</span><span class="sxs-lookup"><span data-stu-id="f7926-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

#### <a name="details"></a><span data-ttu-id="f7926-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f7926-102">Details</span></span>

<span data-ttu-id="f7926-103">Zprávy ve webových službách WCF hostované v Internetová informační služba (IIS) nebo ve vývojovém serveru ASP.NET, který překračuje maxRequestLength (v ASP.NET) nebo třídy maxReceivedMessageSize (ve službě WCF), mají rozdílnou chybu codeThe stavový kód HTTP se změnil z 400 (chybný požadavek) na 413 (příliš velký požadavek entity) a zprávy, které překračují buď maxRequestLength nebo nastavení třídy maxReceivedMessageSize, vyvolávají <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> výjimku.</span><span class="sxs-lookup"><span data-stu-id="f7926-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="f7926-104">To zahrnuje případy, ve kterých je Přenosový režim streamování.</span><span class="sxs-lookup"><span data-stu-id="f7926-104">This includes cases in which the transfer mode is Streamed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7926-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="f7926-105">Suggestion</span></span>

<span data-ttu-id="f7926-106">Tato změna usnadňuje ladění v případech, kde délka zprávy překročí limity povolené ASP.NET nebo WCF. Je třeba upravit jakýkoli kód, který provádí zpracování na základě kódu stavu HTTP 400.</span><span class="sxs-lookup"><span data-stu-id="f7926-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>

| <span data-ttu-id="f7926-107">Name</span><span class="sxs-lookup"><span data-stu-id="f7926-107">Name</span></span>    | <span data-ttu-id="f7926-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f7926-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f7926-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f7926-109">Scope</span></span>   |<span data-ttu-id="f7926-110">Edge</span><span class="sxs-lookup"><span data-stu-id="f7926-110">Edge</span></span>|
|<span data-ttu-id="f7926-111">Verze</span><span class="sxs-lookup"><span data-stu-id="f7926-111">Version</span></span>|<span data-ttu-id="f7926-112">4.5</span><span class="sxs-lookup"><span data-stu-id="f7926-112">4.5</span></span>|
|<span data-ttu-id="f7926-113">Typ</span><span class="sxs-lookup"><span data-stu-id="f7926-113">Type</span></span>|<span data-ttu-id="f7926-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f7926-114">Runtime</span></span>|
