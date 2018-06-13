---
title: Obecné typy v běhovém prostředí (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: c7cc0580398eeb5c70422cba3569340133107b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334532"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Obecné typy v běhovém prostředí (Průvodce programováním v C#)
Když je obecný typ nebo metoda zkompilován Microsoft (MSIL intermediate language), obsahuje metadata, která ji identifikuje jako s parametry typu. Jak MSIL pro obecný typ se používá, se liší podle toho, zda zadaný typ parametru hodnotu typu nebo typu odkazu.  
  
 -Li obecného typu nejprve vytvořená s typem hodnotu jako parametr, modul runtime vytvoří specializované obecného typu s zadaný parametrem nebo nahrazena v vhodného umístění v MSIL parametry. Specializované obecné typy jsou vytvořeny jednou pro každou jedinečnou hodnotu typ, který se používá jako parametr.  
  
 Předpokládejme například, program kódu deklarovaný zásobníku, který je sestavený celých čísel:  
  
 [!code-csharp[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 V tomto okamžiku modul runtime generuje specializovanou verzi <xref:System.Collections.Generic.Stack%601> třídu, která je nahrazena příslušným způsobem pro její parametr celé číslo. Nyní, vždy, když program kód používá zásobník celých čísel, vygenerovaného runtime opětné specializuje <xref:System.Collections.Generic.Stack%601> třídy. V následujícím příkladu jsou vytvořeny dva instance zásobníku celých čísel a sdílejí jednu instanci `Stack<int>` kódu:  
  
 [!code-csharp[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 Však Předpokládejme, že jiný <xref:System.Collections.Generic.Stack%601> třídy s typem jinou hodnotu, jako `long` nebo strukturou uživatelem definované jako její parametr bude vytvořena na jiné místo v kódu. V důsledku toho modul runtime generuje jinou verzi aplikace obecného typu a nahradí `long` do vhodného umístění v MSIL. Převody již nejsou potřebné protože každá specializované obecná třída nativně obsahuje typ hodnoty.  
  
 Obecné typy fungují trochu jinak pro odkazové typy. Při prvním obecného typu je vytvořený pomocí libovolného typu odkaz, modul runtime vytvoří s odkazy na objekty nahrazena pro parametry v MSIL specializované obecného typu. Potom pokaždé, když vytvoření instance typu sestavené s typu odkaz jako svůj parametr bez ohledu na to, jaký typ je modul runtime opětovně používá dříve vytvořenou specializovanou verzi obecného typu. To je možné, protože všechny odkazy mají stejnou velikost.  
  
 Předpokládejme například, že jste měli dva typy odkazů `Customer` třídy a `Order` třídy a také Předpokládejme, že jste vytvořili více `Customer` typy:  
  
 [!code-csharp[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-csharp[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 V tomto okamžiku modul runtime generuje specializovanou verzi <xref:System.Collections.Generic.Stack%601> třídu, která ukládá odkazy na objekty, které budou vyplněna později místo ukládání dat. Předpokládejme, že dalším řádku kódu vytvoří zásobníku jiného typu odkaz, který se nazývá `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 Na rozdíl od s typy hodnot, jiné specializuje verzi <xref:System.Collections.Generic.Stack%601> třída není vytvořena pro `Order` typu. Místo toho instanci specializovanou verzi <xref:System.Collections.Generic.Stack%601> vytvořit třídu a `orders` proměnná je nastavená na něj odkazovat. Předpokládejme, pak zjistil řádek kód k vytvoření zásobník `Customer` typu:  
  
 [!code-csharp[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 Stejně jako u předchozí použití <xref:System.Collections.Generic.Stack%601> třída vytvořili pomocí `Order` zadejte jinou instanci specializované <xref:System.Collections.Generic.Stack%601> vytvořit třídu. Ukazatele, které jsou obsaženy v něm jsou nastavené tak, aby odkazovaly na oblast paměti velikost `Customer` typu. Vzhledem k tomu, že počet typů odkaz se může měnit programu velkým, implementace C# obecných typů výrazně snižuje velikost kód na jedno snížením počtu specializované tříd vytvořené kompilátoru pro obecné třídy odkazové typy.  
  
 Kromě toho při vytváření instance obecné třídy jazyka C# s použitím parametru hodnoty typu nebo odkaz na typ reflexe můžete dotazovat za běhu a jeho skutečný typ a její typ parametru lze zjistit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Obecné typy](~/docs/standard/generics/index.md)
