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
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216300"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
Aktivuje se Pomocník s `invalidMemberDeclaration`em spravovaného ladění (MDA), který nahlásí chybu, ke které dojde při určení způsobu zařazení parametrů člena, který se má volat z modelu COM.  
  
## <a name="symptoms"></a>Příznaky  
 Neúspěšná hodnota HRESULT se vrátí do modelu COM bez volání spravované metody.  
  
## <a name="cause"></a>Příčina  
 Nejpravděpodobnější příčinou je nekompatibilní atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> u jednoho z parametrů.  
  
## <a name="resolution"></a>Řešení  
 Zadejte platné atributy <xref:System.Runtime.InteropServices.MarshalAsAttribute> u parametrů.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Informační zpráva obsahující název člena, název typu a chybovou zprávu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
