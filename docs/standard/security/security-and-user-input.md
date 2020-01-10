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
ms.openlocfilehash: 0d34b06b44241feb7d6e3c8f76447b861563cfdc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705857"
---
# <a name="security-and-user-input"></a><span data-ttu-id="535c5-102">Zabezpečení a uživatelský vstup</span><span class="sxs-lookup"><span data-stu-id="535c5-102">Security and User Input</span></span>

<span data-ttu-id="535c5-103">Data uživatelů, což je jakýkoli druh vstupu (data z webového požadavku nebo adresy URL, vstup do ovládacích prvků aplikace Microsoft model Windows Forms a tak dále), mohou nepříznivě ovlivňovat kód, protože často se data používají přímo jako parametry pro volání jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="535c5-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="535c5-104">Tato situace je podobná škodlivému kódu volajícímu kód s neobvyklými parametry a je třeba vzít v nich stejná preventivní opatření.</span><span class="sxs-lookup"><span data-stu-id="535c5-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="535c5-105">Vstup uživatele je ve skutečnosti těžší, protože není k dispozici žádný rámec zásobníku pro trasování přítomnosti potenciálně nedůvěryhodných dat.</span><span class="sxs-lookup"><span data-stu-id="535c5-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="535c5-106">Tyto chyby jsou z nejtěžších a nejzávažnější chyb zabezpečení, protože mohou existovat v kódu, který je zdánlivě nesouvisející se zabezpečením, jedná se o bránu pro předávání chybných dat do jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="535c5-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="535c5-107">Pokud chcete vyhledat tyto chyby, použijte libovolný druh vstupních dat, Představte si, co může být rozsah možných hodnot, a zvažte, jestli kód, který tato data zobrazuje, může zpracovat všechny tyto případy.</span><span class="sxs-lookup"><span data-stu-id="535c5-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="535c5-108">Tyto chyby můžete opravit přes kontrolu rozsahu a odmítnutí jakéhokoli vstupu, který kód nemůže zpracovat.</span><span class="sxs-lookup"><span data-stu-id="535c5-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="535c5-109">Mezi důležité důležité informace týkající se uživatelských dat patří následující:</span><span class="sxs-lookup"><span data-stu-id="535c5-109">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="535c5-110">Veškerá uživatelská data v reakci serveru běží v kontextu lokality serveru v klientovi.</span><span class="sxs-lookup"><span data-stu-id="535c5-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="535c5-111">Pokud váš webový server přebírá data uživatelů a vkládá je do vrácené webové stránky, může například zahrnovat **> značku skriptu\<** a spustit jako if ze serveru.</span><span class="sxs-lookup"><span data-stu-id="535c5-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="535c5-112">Pamatujte, že klient si může vyžádat libovolnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="535c5-112">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="535c5-113">Zvažte štych nebo neplatné cesty:</span><span class="sxs-lookup"><span data-stu-id="535c5-113">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="535c5-114">.. \, extrémně dlouhé cesty.</span><span class="sxs-lookup"><span data-stu-id="535c5-114">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="535c5-115">Použití zástupných znaků (\*).</span><span class="sxs-lookup"><span data-stu-id="535c5-115">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="535c5-116">Rozšíření tokenu (% token%)</span><span class="sxs-lookup"><span data-stu-id="535c5-116">Token expansion (%token%).</span></span>

  - <span data-ttu-id="535c5-117">Podivné formy cest se zvláštními významy.</span><span class="sxs-lookup"><span data-stu-id="535c5-117">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="535c5-118">Alternativní názvy datových proudů systému souborů, například `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="535c5-118">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="535c5-119">Krátké verze názvů souborů, například `longfi~1` pro `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="535c5-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="535c5-120">Mějte na paměti, že Eval (UserData) může dělat cokoli.</span><span class="sxs-lookup"><span data-stu-id="535c5-120">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="535c5-121">Přistupují opatrně pozdní vazby na název, který obsahuje některá uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="535c5-121">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="535c5-122">Pokud pracujete s webovými daty, vezměte v úvahu různé formy řídicích znaků, které jsou povolené, včetně:</span><span class="sxs-lookup"><span data-stu-id="535c5-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="535c5-123">Šestnáctkové řídicí znaky (% NN).</span><span class="sxs-lookup"><span data-stu-id="535c5-123">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="535c5-124">Řídicí znaky Unicode (% NNN).</span><span class="sxs-lookup"><span data-stu-id="535c5-124">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="535c5-125">Nenáročné řídicí sekvence UTF-8 (% NN% NN).</span><span class="sxs-lookup"><span data-stu-id="535c5-125">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="535c5-126">Dvojité řídicí znaky (% NN se stávají% mmnn, kde% mm je řídicí znak pro%).</span><span class="sxs-lookup"><span data-stu-id="535c5-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="535c5-127">Přistupují opatrně uživatelských jmen, která mohou mít více než jeden Kanonický formát.</span><span class="sxs-lookup"><span data-stu-id="535c5-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="535c5-128">Například můžete často použít buď formulář MYDOMAIN\\*username* , nebo formulář *username*@mydomain.example.com.</span><span class="sxs-lookup"><span data-stu-id="535c5-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="535c5-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="535c5-129">See also</span></span>

- [<span data-ttu-id="535c5-130">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="535c5-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
