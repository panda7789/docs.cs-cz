---
title: "Vstupní znakovou sadu (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1a830d9df1f94bd21689cba9a9893cb9c344dfdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="98ccd-102">Vstupní znakovou sadu (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="98ccd-102">Input Character Set (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="98ccd-103">přijme kódovaný v UTF-16 znaků UNICODE.</span><span class="sxs-lookup"><span data-stu-id="98ccd-103"> accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="98ccd-104">Textové literály může obsahovat libovolný znak UTF-16 uzavřená do jednoduchých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="98ccd-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="98ccd-105">Například N '文字列リテラル'.</span><span class="sxs-lookup"><span data-stu-id="98ccd-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="98ccd-106">Při porovnání textové literály, použijí se původní hodnoty UTF-16.</span><span class="sxs-lookup"><span data-stu-id="98ccd-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="98ccd-107">Například N'ABC, se liší v japonské a Latin kódové stránky.</span><span class="sxs-lookup"><span data-stu-id="98ccd-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="98ccd-108">Komentáře mohou obsahovat libovolný znak UTF-16.</span><span class="sxs-lookup"><span data-stu-id="98ccd-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="98ccd-109">Identifikátory uvozené řídicími znaky může obsahovat libovolný znak UTF-16 uzavřeny do hranatých závorek.</span><span class="sxs-lookup"><span data-stu-id="98ccd-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="98ccd-110">Například [エスケープされた識別子].</span><span class="sxs-lookup"><span data-stu-id="98ccd-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="98ccd-111">Porovnání identifikátory uvozené UTF-16 nejsou rozlišována malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="98ccd-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="98ccd-112">zpracovává verzích písmena, která zobrazí stejné, ale jsou z jiné znakové stránky jako jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="98ccd-112"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="98ccd-113">Například je ekvivalentní [abc] [ABC], pokud odpovídající znaky ze stejné znaková stránka.</span><span class="sxs-lookup"><span data-stu-id="98ccd-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="98ccd-114">Pokud stejný dva identifikátory z jiné znakové stránky, jsou to ale není ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="98ccd-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="98ccd-115">Prázdné místo je libovolný znak prázdné znaky znakové sady UTF-16.</span><span class="sxs-lookup"><span data-stu-id="98ccd-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="98ccd-116">Nový řádek je všechny normalizovaný znak nového řádku UTF-16.</span><span class="sxs-lookup"><span data-stu-id="98ccd-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="98ccd-117">Například '\n' a '\r\n, jsou považovány za znaky nového řádku, ale '\r' není znak nového řádku.</span><span class="sxs-lookup"><span data-stu-id="98ccd-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="98ccd-118">Klíčová slova, výrazy a interpunkční znaménka, může být libovolný znak UTF-16, který normalizuje k Latin.</span><span class="sxs-lookup"><span data-stu-id="98ccd-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="98ccd-119">Například vyberte v japonské znaková stránka je platný – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="98ccd-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="98ccd-120">Klíčová slova, výrazy a interpunkce lze pouze znaky latinky.</span><span class="sxs-lookup"><span data-stu-id="98ccd-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="98ccd-121">`SELECT`v japonské kódová stránka není klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="98ccd-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="98ccd-122">+,-, *, /, =, (,), ", [,] a dalších jazyk konstrukce není v uvozovkách zde lze pouze znaky latinky.</span><span class="sxs-lookup"><span data-stu-id="98ccd-122">+, -, *, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="98ccd-123">Jednoduché identifikátory lze pouze znaky latinky.</span><span class="sxs-lookup"><span data-stu-id="98ccd-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="98ccd-124">Tím je zabráněno nejednoznačnosti při porovnávání, protože se pak porovnávají původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="98ccd-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="98ccd-125">Například by být ABC liší v japonské a Latin kódové stránky.</span><span class="sxs-lookup"><span data-stu-id="98ccd-125">For example, ABC would be different in in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ccd-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="98ccd-126">See Also</span></span>  
 [<span data-ttu-id="98ccd-127">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="98ccd-127">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
