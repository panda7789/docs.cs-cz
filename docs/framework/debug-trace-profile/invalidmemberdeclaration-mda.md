---
title: invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe15d718a9c5f91bfae4f37c04e726990e2fbd45
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052588"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
Je aktivován pomocník spravovaného ladění (MDA), který nahlásí chybu, ke které dojde při určení způsobu zařazení parametrů člena, který se má volat z modelu COM. `invalidMemberDeclaration`  
  
## <a name="symptoms"></a>Příznaky  
 Neúspěšná hodnota HRESULT se vrátí do modelu COM bez volání spravované metody.  
  
## <a name="cause"></a>příčina  
 Nejpravděpodobnější příčinou je nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut u jednoho z parametrů.  
  
## <a name="resolution"></a>Řešení  
 Zadejte platné <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy pro parametry.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Informační zpráva obsahující název člena, název typu a chybovou zprávu.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
