---
title: Zabezpečení a uživatelský vstup
description: Váš kód může předat uživatelem zadaná data jako parametry do jiného kódu, což může mít vliv na zabezpečení. Můžete provést kontrolu rozsahu a zamítnout problematický vstup.
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: e46bf8e653567637b4e6236849981fdb32df447c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555939"
---
# <a name="security-and-user-input"></a><span data-ttu-id="a14b7-104">Zabezpečení a uživatelský vstup</span><span class="sxs-lookup"><span data-stu-id="a14b7-104">Security and User Input</span></span>

<span data-ttu-id="a14b7-105">Data uživatelů, což je jakýkoli druh vstupu (data z webového požadavku nebo adresy URL, vstup do ovládacích prvků aplikace Microsoft model Windows Forms a tak dále), mohou nepříznivě ovlivňovat kód, protože často se data používají přímo jako parametry pro volání jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="a14b7-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="a14b7-106">Tato situace je podobná škodlivému kódu volajícímu kód s neobvyklými parametry a je třeba vzít v nich stejná preventivní opatření.</span><span class="sxs-lookup"><span data-stu-id="a14b7-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="a14b7-107">Vstup uživatele je ve skutečnosti těžší, protože není k dispozici žádný rámec zásobníku pro trasování přítomnosti potenciálně nedůvěryhodných dat.</span><span class="sxs-lookup"><span data-stu-id="a14b7-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="a14b7-108">Tyto chyby jsou z nejtěžších a nejzávažnější chyb zabezpečení, protože mohou existovat v kódu, který je zdánlivě nesouvisející se zabezpečením, jedná se o bránu pro předávání chybných dat do jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="a14b7-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="a14b7-109">Pokud chcete vyhledat tyto chyby, použijte libovolný druh vstupních dat, Představte si, co může být rozsah možných hodnot, a zvažte, jestli kód, který tato data zobrazuje, může zpracovat všechny tyto případy.</span><span class="sxs-lookup"><span data-stu-id="a14b7-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="a14b7-110">Tyto chyby můžete opravit přes kontrolu rozsahu a odmítnutí jakéhokoli vstupu, který kód nemůže zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a14b7-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="a14b7-111">Mezi důležité důležité informace týkající se uživatelských dat patří následující:</span><span class="sxs-lookup"><span data-stu-id="a14b7-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="a14b7-112">Veškerá uživatelská data v reakci serveru běží v kontextu lokality serveru v klientovi.</span><span class="sxs-lookup"><span data-stu-id="a14b7-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="a14b7-113">Pokud váš webový server přebírá data uživatelů a vkládá je do vrácené webové stránky, může například obsahovat **\<script>** značku a spustit jako if ze serveru.</span><span class="sxs-lookup"><span data-stu-id="a14b7-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="a14b7-114">Pamatujte, že klient si může vyžádat libovolnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="a14b7-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="a14b7-115">Zvažte štych nebo neplatné cesty:</span><span class="sxs-lookup"><span data-stu-id="a14b7-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="a14b7-116">.. \, extrémně dlouhé cesty.</span><span class="sxs-lookup"><span data-stu-id="a14b7-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="a14b7-117">Použití zástupných znaků (\*).</span><span class="sxs-lookup"><span data-stu-id="a14b7-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="a14b7-118">Rozšíření tokenu (% token%)</span><span class="sxs-lookup"><span data-stu-id="a14b7-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="a14b7-119">Podivné formy cest se zvláštními významy.</span><span class="sxs-lookup"><span data-stu-id="a14b7-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="a14b7-120">Alternativní názvy datových proudů systému souborů, jako je například `filename::$DATA` .</span><span class="sxs-lookup"><span data-stu-id="a14b7-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="a14b7-121">Krátké verze názvů souborů, například `longfi~1` pro `longfilename` .</span><span class="sxs-lookup"><span data-stu-id="a14b7-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="a14b7-122">Mějte na paměti, že Eval (UserData) může dělat cokoli.</span><span class="sxs-lookup"><span data-stu-id="a14b7-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="a14b7-123">Přistupují opatrně pozdní vazby na název, který obsahuje některá uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="a14b7-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="a14b7-124">Pokud pracujete s webovými daty, vezměte v úvahu různé formy řídicích znaků, které jsou povolené, včetně:</span><span class="sxs-lookup"><span data-stu-id="a14b7-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="a14b7-125">Šestnáctkové řídicí znaky (% NN).</span><span class="sxs-lookup"><span data-stu-id="a14b7-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="a14b7-126">Řídicí znaky Unicode (% NNN).</span><span class="sxs-lookup"><span data-stu-id="a14b7-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="a14b7-127">Nenáročné řídicí sekvence UTF-8 (% NN% NN).</span><span class="sxs-lookup"><span data-stu-id="a14b7-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="a14b7-128">Dvojité řídicí znaky (% NN se stávají% mmnn, kde% mm je řídicí znak pro%).</span><span class="sxs-lookup"><span data-stu-id="a14b7-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="a14b7-129">Přistupují opatrně uživatelských jmen, která mohou mít více než jeden Kanonický formát.</span><span class="sxs-lookup"><span data-stu-id="a14b7-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="a14b7-130">Například můžete často použít buď formulář MYDOMAIN \\ *username* , nebo formulář *username* @mydomain.example.com .</span><span class="sxs-lookup"><span data-stu-id="a14b7-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="a14b7-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a14b7-131">See also</span></span>

- [<span data-ttu-id="a14b7-132">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="a14b7-132">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="a14b7-133">ASP.NET Core zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a14b7-133">ASP.NET Core Security</span></span>](/aspnet/core/security/)
