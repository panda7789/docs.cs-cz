---
title: Metody System.String
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: c988bf7f04b284b0d352cd9e495931543980fdba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613744"
---
# <a name="systemstring-methods"></a><span data-ttu-id="46931-102">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="46931-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="46931-103">nepodporuje následující <xref:System.String> metody.</span><span class="sxs-lookup"><span data-stu-id="46931-103">does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="46931-104">Obecně nepodporované metody System.String</span><span class="sxs-lookup"><span data-stu-id="46931-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="46931-105">Nepodporovaná <xref:System.String> v obecné metody:</span><span class="sxs-lookup"><span data-stu-id="46931-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
- <span data-ttu-id="46931-106">Zohledňující jazykovou verzi přetížení (metody, které přebírají `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="46931-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
- <span data-ttu-id="46931-107">Metody, které trvat nebo vytvářet `char` pole.</span><span class="sxs-lookup"><span data-stu-id="46931-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="46931-108">Nepodporovaná System.String statické metody</span><span class="sxs-lookup"><span data-stu-id="46931-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="46931-109">Nepodporovaná System.String statické metody</span><span class="sxs-lookup"><span data-stu-id="46931-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="46931-110">Nepodporovaná System.String nestatických metod</span><span class="sxs-lookup"><span data-stu-id="46931-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="46931-111">Nepodporovaná System.String nestatických metod</span><span class="sxs-lookup"><span data-stu-id="46931-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="46931-112">Rozdíl oproti .NET</span><span class="sxs-lookup"><span data-stu-id="46931-112">Differences from .NET</span></span>  
  
- <span data-ttu-id="46931-113">Dotazy nespadá kolací systému SQL Server, které může být výsledkem bude na serveru a proto bude poskytovat Porovnání zohledňující jazykovou verzi, velká a malá písmena ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="46931-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="46931-114">Toto chování se liší od výchozí malá a velká písmena sémantiku rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46931-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
- <span data-ttu-id="46931-115">Když `LastIndexOf` vrátí hodnotu 0, řetězec je `NULL` nebo nalezený pozice je 0.</span><span class="sxs-lookup"><span data-stu-id="46931-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
- <span data-ttu-id="46931-116">Může vrátit neočekávané výsledky ze zřetězení nebo jiné operace na řetězce pevné délky (`CHAR`, `NCHAR`), protože tyto typy mají automaticky odsazení použijí v databázi.</span><span class="sxs-lookup"><span data-stu-id="46931-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
- <span data-ttu-id="46931-117">Protože mnoho metod, jako `Replace`, `ToLower`, `ToUpper`a indexeru znaků, obsahovat žádný platný překlad pro `TEXT` nebo `NTEXT` sloupce a XML, `SqlExceptions` dojít, pokud obvykle přeložit.</span><span class="sxs-lookup"><span data-stu-id="46931-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="46931-118">Toto chování se považuje za přijatelné pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="46931-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="46931-119">Nicméně všechny operace s řetězci musí odpovídat common language runtime (CLR) Sémantika pro `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, a `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="46931-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46931-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46931-120">See also</span></span>

- [<span data-ttu-id="46931-121">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="46931-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
