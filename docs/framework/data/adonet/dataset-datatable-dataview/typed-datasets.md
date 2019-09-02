---
title: Typové datové sady
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 33876cb9f614a93cab2fa3fd9d056f94dd1e9038
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203162"
---
# <a name="typed-datasets"></a><span data-ttu-id="a512a-102">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="a512a-102">Typed DataSets</span></span>
<span data-ttu-id="a512a-103">Společně s přístupem s pozdní vazbou k hodnotám prostřednictvím slabých typových proměnných <xref:System.Data.DataSet> poskytuje přístup k datům prostřednictvím silného typu metafora.</span><span class="sxs-lookup"><span data-stu-id="a512a-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="a512a-104">Tabulky a sloupce, které jsou součástí **datové sady** , mohou být k dispozici pomocí uživatelsky přívětivých názvů a proměnných se silným typem.</span><span class="sxs-lookup"><span data-stu-id="a512a-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="a512a-105">Typová **datová sada** je třída, která je odvozena z **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="a512a-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="a512a-106">V takovém případě dědí všechny metody, události a vlastnosti **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="a512a-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="a512a-107">Kromě toho typová **datová sada** poskytuje metody, události a vlastnosti silného typu.</span><span class="sxs-lookup"><span data-stu-id="a512a-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="a512a-108">To znamená, že můžete získat přístup k tabulkám a sloupcům podle názvu namísto použití metod založených na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="a512a-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="a512a-109">Kromě zlepšení čitelnosti kódu umožňuje typová **datová sada** také editoru kódu sady Visual Studio .NET automatické dokončování řádků při psaní.</span><span class="sxs-lookup"><span data-stu-id="a512a-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="a512a-110">**Datová sada** silného typu navíc poskytuje přístup k hodnotám jako správný typ v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a512a-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="a512a-111">V případě silně typované **datové sady**jsou zachyceny chyby neshody typů, pokud je kód zkompilován, nikoli za běhu.</span><span class="sxs-lookup"><span data-stu-id="a512a-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a512a-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a512a-112">In This Section</span></span>  
 [<span data-ttu-id="a512a-113">Generování datových sad se silnými typy</span><span class="sxs-lookup"><span data-stu-id="a512a-113">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="a512a-114">Popisuje, jak vytvořit a použít typovou datovou **sadu**se silnými typy.</span><span class="sxs-lookup"><span data-stu-id="a512a-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="a512a-115">Zadávání poznámek k typovým datovým sadám</span><span class="sxs-lookup"><span data-stu-id="a512a-115">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="a512a-116">Popisuje, jak opatřit poznámkami schéma XML schématu definice jazyka (XSD) používané k vygenerování **datové sady**se silnými typy , aby byly uživatelsky přívětivé názvy přizpůsobitelné bez změny podkladového schématu.</span><span class="sxs-lookup"><span data-stu-id="a512a-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a512a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a512a-117">See also</span></span>

- [<span data-ttu-id="a512a-118">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="a512a-118">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a512a-119">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a512a-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
