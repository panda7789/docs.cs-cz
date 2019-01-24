---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 334bab97a04ed464dce6944692b04a9ed1295296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613818"
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
