---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963160"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior
MustUnderstandBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída MustUnderstandBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída MustUnderstandBehavior má následující vlastnost:  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Když `true`, všechna SOAP záhlaví s `MustUnderstand` atributu, která nejsou ovládány způsobí, že chování vyvolání výjimky.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
