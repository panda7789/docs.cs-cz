---
title: Zařazování různých typů polí
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62958f1656dfbfcb45356378161090b8271b6b83
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-different-types-of-arrays"></a>Zařazování různých typů polí
Pole je typu odkazu ve spravovaném kódu, který obsahuje jeden či více elementů stejného typu. I když pole jsou odkazové typy, je jsou předat jako parametry k nespravovaným funkcím. Toto chování je konzistentní způsob spravovaných polí jsou předávány spravovaných objektů, což je jako vstupně -výstupní parametry. Další podrobnosti najdete v tématu [kopírování a přichycování](copying-and-pinning.md).  
  
 V následující tabulce je uveden seznam možností zařazování pro pole a popisuje jejich použití.  
  
|Pole|Popis|  
|-----------|-----------------|  
|Celých čísel hodnotou.|Jako parametr v předá pole celých čísel.|  
|Celých čísel odkazem.|Pole celých čísel předá jako parametr v nebo na více systémů.|  
|Celých čísel podle hodnoty (dvourozměrná).|Předá jako parametr v matici celých čísel.|  
|Řetězce podle hodnoty.|Jako parametr v předá pole řetězců.|  
|Struktur s celými čísly.|Předá pole struktury, které obsahují celá čísla jako parametr v.|  
|Struktur s řetězci.|Předá pole struktury, které obsahují jenom celá čísla jako parametr v nebo na více systémů. Členy pole lze změnit.|  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak následující typy polí:  
  
-   Pole celých čísel hodnotou.  
  
-   Pole celých čísel podle odkaz, který jde změnit.  
  
-   Vícerozměrná pole (matice) celých čísel hodnotou.  
  
-   Pole řetězců hodnotou.  
  
-   Pole struktur s celými čísly.  
  
-   Pole struktur s řetězci.  
  
 Pokud pole není explicitně zařazena pomocí odkazu, použije se výchozí chování zařazuje jako parametr v poli. Toto chování lze změnit použitím <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> explicitně atributy.  
  
 Pole – Ukázka používá následující nespravované funkce s jejich původní deklarace funkce:  
  
-   **TestArrayOfInts** exportovaný z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   **TestRefArrayOfInts** exportovaný z PinvokeLib.dll.  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   **TestMatrixOfInts** exportovaný z PinvokeLib.dll.  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   **TestArrayOfStrings** exportovaný z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   **TestArrayOfStructs** exportovaný z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   **TestArrayOfStructs2** exportovaný z PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementace pro výše uvedených funkcí a dvě proměnné struktury **MYPOINT** a **MYPERSON**. Struktury obsahovat tyto prvky:  
  
```  
typedef struct _MYPOINT  
{  
   int x;   
   int y;   
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON;  
```  
  
 V této ukázce `MyPoint` a `MyPerson` struktury obsahovat vložené typy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Je nastavena na hodnotu zabezpečit, aby členové jsou uspořádány v paměti postupně, v pořadí, ve kterém jsou zobrazeny.  
  
 `LibWrap` Třída obsahuje sadu volá metody `App` třídy. Konkrétní podrobnosti o předávání polí najdete v tématu komentáře v následující ukázce. Pole, která je typu odkazu, je předaná jako parametr v ve výchozím nastavení. Pro volající získat výsledky **InAttribute** a **OutAttribute** musí být použita explicitně argument obsahující pole.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Viz také  
 [Zařazování pole typů](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
