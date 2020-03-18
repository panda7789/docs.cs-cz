---
title: Zabezpečení a uživatelský vstup
description: Váš kód může předat uživatelem zadaná data jako parametry jinému kódu, což může ovlivnit zabezpečení. Můžete provést kontrolu rozsahu a odmítnout problematický vstup.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186110"
---
# <a name="security-and-user-input"></a><span data-ttu-id="94a5b-104">Zabezpečení a uživatelský vstup</span><span class="sxs-lookup"><span data-stu-id="94a5b-104">Security and User Input</span></span>

<span data-ttu-id="94a5b-105">Uživatelská data, což je jakýkoli druh vstupu (data z webového požadavku nebo adresy URL, vstup do ovládacích prvků aplikace Microsoft Windows Forms a tak dále), mohou nepříznivě ovlivnit kód, protože často se tato data používají přímo jako parametry pro volání jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="94a5b-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="94a5b-106">Tato situace je obdobou škodlivého kódu, který volá váš kód s podivnými parametry, a měla by být přijata stejná opatření.</span><span class="sxs-lookup"><span data-stu-id="94a5b-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="94a5b-107">Vstup uživatele je ve skutečnosti těžší, aby bezpečné, protože neexistuje žádný rámec zásobníku sledovat přítomnost potenciálně nedůvěryhodných dat.</span><span class="sxs-lookup"><span data-stu-id="94a5b-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="94a5b-108">Jedná se o jedny z nejjemnějších a nejtěžších chyb zabezpečení, které lze najít, protože i když mohou existovat v kódu, který zdánlivě nesouvisí se zabezpečením, jsou bránou pro předání chybná data do jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="94a5b-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="94a5b-109">Chcete-li hledat tyto chyby, postupujte podle jakéhokoli druhu vstupních dat, představte si, jaký rozsah možných hodnot může být a zvažte, zda kód, který vidí tato data, může zpracovat všechny tyto případy.</span><span class="sxs-lookup"><span data-stu-id="94a5b-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="94a5b-110">Tyto chyby můžete opravit kontrolou rozsahu a odmítnutím jakéhokoli vstupu, který kód nemůže zpracovat.</span><span class="sxs-lookup"><span data-stu-id="94a5b-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="94a5b-111">Některé důležité aspekty týkající se uživatelských dat zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="94a5b-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="94a5b-112">Všechna uživatelská data v odpovědi serveru jsou spuštěna v kontextu serveru v klientovi.</span><span class="sxs-lookup"><span data-stu-id="94a5b-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="94a5b-113">Pokud webový server přebírá uživatelská data a vkládá je na vrácenou webovou stránku, může například obsahovat \*\* \<značku skriptu>\*\* a spustit jako by ze serveru.</span><span class="sxs-lookup"><span data-stu-id="94a5b-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="94a5b-114">Nezapomeňte, že klient může požádat o libovolnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="94a5b-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="94a5b-115">Zvažte složité nebo neplatné cesty:</span><span class="sxs-lookup"><span data-stu-id="94a5b-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="94a5b-116">.. \ , extrémně dlouhé cesty.</span><span class="sxs-lookup"><span data-stu-id="94a5b-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="94a5b-117">Použití zástupných znaků (\*).</span><span class="sxs-lookup"><span data-stu-id="94a5b-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="94a5b-118">Rozšíření tokenu (%token%).</span><span class="sxs-lookup"><span data-stu-id="94a5b-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="94a5b-119">Podivné formy cest se zvláštním významem.</span><span class="sxs-lookup"><span data-stu-id="94a5b-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="94a5b-120">Alternativní názvy datových `filename::$DATA`proudů systému souborů, například .</span><span class="sxs-lookup"><span data-stu-id="94a5b-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="94a5b-121">Krátké verze názvů souborů, `longfi~1` `longfilename`například pro .</span><span class="sxs-lookup"><span data-stu-id="94a5b-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="94a5b-122">Nezapomeňte, že Eval(userdata) může dělat cokoliv.</span><span class="sxs-lookup"><span data-stu-id="94a5b-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="94a5b-123">Buďte opatrní pozdní vazby na název, který obsahuje některá uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="94a5b-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="94a5b-124">Pokud máte co do činění s webovými daty, zvažte různé formy úniky, které jsou přípustné, včetně:</span><span class="sxs-lookup"><span data-stu-id="94a5b-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="94a5b-125">Šestnáctkové úniky (%nn).</span><span class="sxs-lookup"><span data-stu-id="94a5b-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="94a5b-126">Unicode unikne (%nnn).</span><span class="sxs-lookup"><span data-stu-id="94a5b-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="94a5b-127">Overlong UTF-8 escapes (%nn%nn).</span><span class="sxs-lookup"><span data-stu-id="94a5b-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="94a5b-128">Dvojité uniknutí (%nn se stane %mmnn, kde %mm je escape pro %').</span><span class="sxs-lookup"><span data-stu-id="94a5b-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="94a5b-129">Buďte opatrní na uživatelská jména, která mohou mít více než jeden kanonický formát.</span><span class="sxs-lookup"><span data-stu-id="94a5b-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="94a5b-130">Často můžete například použít formulář\\*uživatelského jména* MYDOMAIN nebo formulář *uživatelského jména.* @mydomain.example.com</span><span class="sxs-lookup"><span data-stu-id="94a5b-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="94a5b-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="94a5b-131">See also</span></span>

- [<span data-ttu-id="94a5b-132">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="94a5b-132">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
