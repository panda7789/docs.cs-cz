---
title: Zabezpečení a uživatelský vstup
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27818d5e1779cd6e10e11830f91a20a3e638639a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933780"
---
# <a name="security-and-user-input"></a><span data-ttu-id="62803-102">Zabezpečení a uživatelský vstup</span><span class="sxs-lookup"><span data-stu-id="62803-102">Security and User Input</span></span>
<span data-ttu-id="62803-103">Uživatelská data, která je jakýkoli druh vstupních (datových z webového požadavku nebo adresu URL, vstupní ovládací prvky aplikace Microsoft Windows Forms a tak dále), může nepříznivě ovlivnit kód, protože často tato data se používají přímo jako parametry pro volání jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="62803-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="62803-104">Tato situace je obdobou škodlivý kód volá váš kód s neznámé parametry a stejná opatření by měl být přijata.</span><span class="sxs-lookup"><span data-stu-id="62803-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="62803-105">Uživatelský vstup je ve skutečnosti obtížnější zabezpečit, protože neexistuje žádný rámce zásobníku trasování na přítomnost potenciálně nedůvěryhodná data.</span><span class="sxs-lookup"><span data-stu-id="62803-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>  
  
 <span data-ttu-id="62803-106">Toto jsou mezi zabezpečení nejdelikátnější a těch nejtěžších chyb najít, protože mohou existovat v kódu, který je zdánlivě nesouvisí se zabezpečením, jsou brána chybná data prostřednictvím předat jiným kódem.</span><span class="sxs-lookup"><span data-stu-id="62803-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="62803-107">K vyhledání těchto chyb, postupujte podle všech typů vstupních dat, představte si, co rozsah možných hodnot může být a zvažte, zda kód zobrazení těchto dat může zpracovávat všechny tyto případy.</span><span class="sxs-lookup"><span data-stu-id="62803-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="62803-108">Můžete vyřešit tyto chyby prostřednictvím rozsah kontroly odhalovat a odmítat jakéhokoliv vstupu, který nemůže zpracovat kód.</span><span class="sxs-lookup"><span data-stu-id="62803-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>  
  
 <span data-ttu-id="62803-109">Některé důležité informace týkající se uživatelská data zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="62803-109">Some important considerations involving user data include the following:</span></span>  
  
- <span data-ttu-id="62803-110">Žádná data uživatelů v odpovědi na serveru běží v kontextu na server lokality na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="62803-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="62803-111">Pokud váš webový server přijímá data uživatele a vloží jej do vrácené webové stránce, může například obsahovat  **\<skript >** označit a spustit jako by ze serveru.</span><span class="sxs-lookup"><span data-stu-id="62803-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>  
  
- <span data-ttu-id="62803-112">Mějte na paměti, že klient může požádat o libovolnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="62803-112">Remember that the client can request any URL.</span></span>  
  
- <span data-ttu-id="62803-113">Vezměte v úvahu cesty záludné nebo je neplatný:</span><span class="sxs-lookup"><span data-stu-id="62803-113">Consider tricky or invalid paths:</span></span>  
  
    - <span data-ttu-id="62803-114">.. \, velmi dlouhé cesty.</span><span class="sxs-lookup"><span data-stu-id="62803-114">..\ , extremely long paths.</span></span>  
  
    - <span data-ttu-id="62803-115">Použití zástupných znaků (\*).</span><span class="sxs-lookup"><span data-stu-id="62803-115">Use of wild card characters (\*).</span></span>  
  
    - <span data-ttu-id="62803-116">Rozšíření token (token %).</span><span class="sxs-lookup"><span data-stu-id="62803-116">Token expansion (%token%).</span></span>  
  
    - <span data-ttu-id="62803-117">Neobvyklé formy cesty se zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="62803-117">Strange forms of paths with special meaning.</span></span>  
  
    - <span data-ttu-id="62803-118">Alternativní názvy stream systému souborů, jako například `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="62803-118">Alternate file system stream names such as `filename::$DATA`.</span></span>  
  
    - <span data-ttu-id="62803-119">Krátká verze názvů souborů, jako `longfi~1` pro `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="62803-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>  
  
- <span data-ttu-id="62803-120">Mějte na paměti, že Eval(userdata) může dělat něco.</span><span class="sxs-lookup"><span data-stu-id="62803-120">Remember that Eval(userdata) can do anything.</span></span>  
  
- <span data-ttu-id="62803-121">Dávejte pozor na název, který obsahuje některá uživatelská data z pozdní vazby.</span><span class="sxs-lookup"><span data-stu-id="62803-121">Be wary of late binding to a name that includes some user data.</span></span>  
  
- <span data-ttu-id="62803-122">Pokud pracujete s daty Web, zvažte možnost různé formy řídící znaky, které jsou přípustné, včetně:</span><span class="sxs-lookup"><span data-stu-id="62803-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>  
  
    - <span data-ttu-id="62803-123">Šestnáctková řídicí sekvence (% nn).</span><span class="sxs-lookup"><span data-stu-id="62803-123">Hexadecimal escapes (%nn).</span></span>  
  
    - <span data-ttu-id="62803-124">Řídicí sekvence Unicode (% nnn).</span><span class="sxs-lookup"><span data-stu-id="62803-124">Unicode escapes (%nnn).</span></span>  
  
    - <span data-ttu-id="62803-125">Příliš dlouhého UTF-8 řídicí sekvence (% nn % nn).</span><span class="sxs-lookup"><span data-stu-id="62803-125">Overlong UTF-8 escapes (%nn%nn).</span></span>  
  
    - <span data-ttu-id="62803-126">Dvojité řídicí sekvence (% nn stane mmnn %, kde je % mm řídicí pro '%').</span><span class="sxs-lookup"><span data-stu-id="62803-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>  
  
- <span data-ttu-id="62803-127">Dávejte pozor na uživatelská jména, která může mít více než jeden kanonický formát.</span><span class="sxs-lookup"><span data-stu-id="62803-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="62803-128">Například můžete často použít buď MOJEDOMÉNA\\*uživatelské jméno* formuláře nebo *uživatelské jméno* @mydomain.example.com formuláře.</span><span class="sxs-lookup"><span data-stu-id="62803-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62803-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62803-129">See also</span></span>

- [<span data-ttu-id="62803-130">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="62803-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
