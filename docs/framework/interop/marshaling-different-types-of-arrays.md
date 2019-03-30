---
title: Zařazování různých typů polí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56ca8e6c077d41552f85b65ba5f6b755165ee11a
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654611"
---
# <a name="marshaling-different-types-of-arrays"></a>Zařazování různých typů polí
Pole je typem odkazu ve spravovaném kódu, který obsahuje jeden nebo víc elementů stejného typu. I když pole jsou typy odkazů, jsou předány jako parametry in k nespravovaným funkcím. Toto chování je konzistentní se způsobem spravovaných polí jsou předány do spravovaných objektů, což je jako vstup a výstup parametry. Další podrobnosti najdete v tématu [kopírování a přichycování](copying-and-pinning.md).  
  
 V následující tabulce jsou uvedeny možnosti zařazování pro pole a popisuje jejich použití.  
  
|Pole|Popis|  
|-----------|-----------------|  
|Celých čísel podle hodnoty.|Pole celých čísel se předá jako parametr In.|  
|Celých čísel podle odkazu.|Pole celých čísel se předá jako parametr In/Out.|  
|Celých čísel podle hodnoty (dvojrozměrné).|Matice celých čísel se předá jako parametr In.|  
|Z řetězce podle hodnoty.|Pole řetězců, které se předá jako parametr In.|  
|Struktury s celými čísly.|Předá pole struktury, které obsahují celých čísel jako parametr In.|  
|Struktury s řetězci.|Předá pole struktur, které obsahují řetězce pouze jako vstupně-výstupní parametr. Členy pole lze změnit.|  
  
## <a name="example"></a>Příklad  
 Tato ukázka demonstruje následující typy polí:  
  
-   Pole celých čísel podle hodnoty.  
  
-   Pole celých čísel podle odkazu, který se dá změnit.  
  
-   Vícerozměrná pole (matice) celých čísel podle hodnoty.  
  
-   Pole řetězců podle hodnoty.  
  
-   Pole struktury s celými čísly.  
  
-   Pole struktury s řetězci.  
  
 Pokud pole je explicitně zařazen podle odkazu, zařazuje výchozí chování pole jako parametr In. Toto chování lze změnit použitím <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy explicitně.  
  
 Ukázka polí používá následující nespravované funkce zobrazené s původní deklarací funkce:  
  
-   **TestArrayOfInts** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   **TestRefArrayOfInts** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   **TestMatrixOfInts** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   **TestArrayOfStrings** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   **TestArrayOfStructs** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   **TestArrayOfStructs2** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [Knihovny PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) je vlastní nespravovaná knihovna, která obsahuje implementace dříve uvedených funkcí a dvě proměnné struktury **MYPOINT** a **MYPERSON**. Struktury obsahují následující prvky:  
  
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
  
 V této ukázce `MyPoint` a `MyPerson` obsahuje vestavěné typy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na Ujistěte se, že členové jsou uspořádáni v paměti sekvenčně, v pořadí, v jakém jsou uvedeny.  
  
 `LibWrap` Třída obsahuje sadu metod, které jsou volány `App` třídy. Konkrétní podrobnosti o předávání polí naleznete v tématu komentáře v následujícím příkladu. Pole, která je typem odkazu, je předán jako parametr In ve výchozím nastavení. Pro volajícího na příjem výsledků **InAttribute** a **OutAttribute** se musí použít explicitní argument obsahující pole.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Viz také:
- [Datové typy vyvolání platformy](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
