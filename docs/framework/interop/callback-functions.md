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
Funkce zpětného volání je kód v rámci spravované aplikace, který pomáhá nespravované funkci DLL dokončit úlohu. Volání funkce zpětného volání přecházejí nepřímo ze spravované aplikace prostřednictvím funkce knihovny DLL a zpět do spravované implementace. Některé z mnoha funkcí knihoven DLL volaných s voláním platformy vyžadují funkci zpětného volání ve spravovaném kódu pro správné fungování.  
  
 Chcete-li volat většinu funkcí knihovny DLL ze spravovaného kódu, vytvořte spravovanou definici funkce a pak ji zavolejte. Proces je jednoduchý.  
  
 Použití funkce knihovny DLL, která vyžaduje funkci zpětného volání, má několik dalších kroků. Nejprve je třeba určit, zda funkce vyžaduje zpětné volání, a to tak, že si prohlédněte dokumentaci k funkci. Dále musíte vytvořit funkci zpětného volání ve spravované aplikaci. Nakonec zavolejte funkci DLL a předejte ukazatel na funkci zpětného volání jako argument.

 Následující obrázek shrnuje funkci zpětného volání a postup implementace:  
  
 ![Diagram znázorňující proces zpětného volání vyvolání platformy](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Funkce zpětného volání jsou ideální pro použití v situacích, kdy se úloha provádí opakovaně. Další běžné použití je s funkcemi výčtu, jako jsou **EnumFontFamilies**, **EnumPrinters**a **EnumWindows** v rozhraní API systému Windows. Funkce **EnumWindows** se zobrazí ve všech stávajících oknech v počítači a voláním funkce zpětného volání provede úkol v každém okně. Pokyny a příklad naleznete v tématu [How to: Implementing Functions](how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Viz také

- [Postupy: Implementace funkcí zpětného volání](how-to-implement-callback-functions.md)
- [Volání funkce DLL](calling-a-dll-function.md)
