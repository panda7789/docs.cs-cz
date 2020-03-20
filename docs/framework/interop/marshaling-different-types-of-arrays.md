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
ms.openlocfilehash: 66c7ba5989952edb55f21aab960ad7395a92ae0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181367"
---
# <a name="marshaling-different-types-of-arrays"></a>Zařazování různých typů polí
Pole je typ odkazu ve spravovaném kódu, který obsahuje jeden nebo více prvků stejného typu. Přestože pole jsou typy odkazů, jsou předány jako V parametry nespravované funkce. Toto chování je v rozporu s způsob, jakým jsou spravovaná pole předávána spravovaným objektům, což je jako parametry In/Out. Další podrobnosti naleznete v [tématu Kopírování a připnutí](copying-and-pinning.md).  
  
 V následující tabulce jsou uvedeny možnosti zařazování polí a popisuje jejich použití.  
  
|Pole|Popis|  
|-----------|-----------------|  
|Celá čísla podle hodnoty.|Předá pole celá čísla jako In parametr.|  
|Celá čísla odkazem.|Předá pole celá čísla jako in/out parametr.|  
|Celá čísla podle hodnoty (dvojrozměrné).|Předá matici celá čísla jako In parametr.|  
|Řetězců podle hodnoty.|Předá pole řetězců jako In parametr.|  
|Struktur s celámi.|Předá pole struktur, které obsahují celá čísla jako In parametr.|  
|Struktur s řetězci.|Předá pole struktur, které obsahují pouze řetězce jako in/out parametr. Členy pole lze změnit.|  
  
## <a name="example"></a>Příklad  
 Tato ukázka ukazuje, jak předat následující typy polí:  
  
- Pole celá čísla podle hodnoty.  
  
- Pole celá čísla podle odkazu, které lze velikost.  
  
- Vícerozměrné pole (matice) celá čísla podle hodnoty.  
  
- Pole řetězců podle hodnoty.  
  
- Pole struktur s celá čísla.  
  
- Pole struktur s řetězci.  
  
 Pokud pole je explicitně zařazenodkaz, výchozí chování zařazuje pole jako In parametr. Toto chování můžete změnit <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> použitím atributů a explicitně.  
  
 Ukázka pole používá následující nespravované funkce zobrazené s jejich původní deklarací funkce:  
  
- **TestArrayOfInts** exportován z souboru PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- **TestRefArrayOfInts** exportován z souboru PinvokeLib.dll.  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- **TestMatrixOfInts** exportován z PinvokeLib.dll.  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- **TestArrayOfStrings** exportovány z souboru PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- **TestArrayOfStructs** exportován z souboru PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** exportován z souboru PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a dvě proměnné struktury, **MYPOINT** a **MYPERSON**. Struktury obsahují následující prvky:  
  
```cpp
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
  
 V této ukázce `MyPoint` `MyPerson` a struktury obsahují vložené typy. Atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> je nastaven tak, aby bylo zajištěno, že členy jsou uspořádány v paměti postupně, v pořadí, ve kterém se zobrazí.  
  
 Třída `NativeMethods` obsahuje sadu metod volaných třídou. `App` Konkrétní podrobnosti o předávání polí naleznete v komentářích v následující ukázce. Pole, které je typem odkazu, je ve výchozím nastavení předáno jako parametr In. Aby volající obdržel výsledky, musí být **inAttribute** a **OutAttribute** explicitně použity na argument obsahující pole.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Volající funkce  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Viz také

- [Platforma vyvolat datové typy](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
