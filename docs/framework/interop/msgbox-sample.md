---
title: "MsgBox – ukázka"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b14ee9c435d36e8d6a49cbfb29a57365bcd42d6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="msgbox-sample"></a>MsgBox – ukázka
Tento příklad znázorňuje, jakým způsobem lze předávat typy řetězců pomocí hodnoty jako parametry In a kdy lze použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> a <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.  
  
 Příklad MsgBox používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:  
  
-   **MessageBox** exportovaný z User32.dll.  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 V tomto příkladu obsahuje třída `LibWrap` spravovaný prototyp pro každou nespravovanou funkci volanou třídou `MsgBoxSample`. Metody spravovaného prototypu `MsgBox`, `MsgBox2` a `MsgBox3` mají pro stejnou nespravovanou funkci odlišné deklarace.  
  
 Deklarace pro příklad `MsgBox2` vytváří v okně se zprávou nesprávný výstup, protože typ znaku, který je zadán jako ANSI, se neshoduje se vstupním bodem `MessageBoxW`, což je název funkce Unicode. Deklarace pro `MsgBox3` vytvoří neshody mezi **EntryPoint**, **CharSet**, a **ExactSpelling** pole. Při zavolání vyvolá pole `MsgBox3` výjimku. Podrobné informace o řetězce pojmenovávání a název zařazování, najdete v části [zadání znaková sada](../../../docs/framework/interop/specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 [Zařazování řetězců](../../../docs/framework/interop/marshaling-strings.md)  
 [Datové typy vyvolání platformy](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Výchozí zařazování pro řetězce](../../../docs/framework/interop/default-marshaling-for-strings.md)  
 [Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Určení znakové sady](../../../docs/framework/interop/specifying-a-character-set.md)
