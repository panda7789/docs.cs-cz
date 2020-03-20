---
title: Funkce zpětného volání
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 8b8bb4dff4f73247282060c0b4fd778ae0169b1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181520"
---
# <a name="callback-functions"></a>Funkce zpětného volání
Funkce zpětného volání je kód v rámci spravované aplikace, který pomáhá nespravované funkci DLL dokončit úlohu. Volání funkce zpětného volání projít nepřímo ze spravované aplikace, prostřednictvím funkce DLL a zpět do spravované implementace. Některé z mnoha funkcí dll volána s vyvolání platformy vyžadují funkci zpětného volání ve spravovaném kódu správně spustit.  
  
 Chcete-li volat většinu funkcí DLL ze spravovaného kódu, vytvořte spravovanou definici funkce a pak ji zavolejte. Tento proces je přímočarý.  
  
 Použití funkce DLL, která vyžaduje funkci zpětného volání, má některé další kroky. Nejprve je nutné určit, zda funkce vyžaduje zpětné volání při pohledu na dokumentaci pro funkci. Dále je třeba vytvořit funkci zpětného volání ve spravované aplikaci. Nakonec zavoláte funkci DLL a předáte ukazatel na funkci zpětného volání jako argument.

 Následující obrázek shrnuje funkci zpětného volání a kroky implementace:  
  
 ![Diagram znázorňující proces zpětného volání platformy.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Funkce zpětného volání jsou ideální pro použití v situacích, ve kterých je úloha prováděna opakovaně. Další běžné použití je s funkcemi výčtu, jako je **například EnumFontFamilies**, **EnumPrinters**a **EnumWindows** v rozhraní API systému Windows. Funkce **EnumWindows** vyjmenovává všechna existující okna v počítači a volá funkci zpětného volání k provedení úlohy v každém okně. Pokyny a příklad najdete v [tématu Jak: Implementace funkcí zpětného volání](how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Viz také

- [Postupy: Implementace funkcí zpětného volání](how-to-implement-callback-functions.md)
- [Volání funkce DLL](calling-a-dll-function.md)
