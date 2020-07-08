---
title: invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Invalidmemberdeclaration –, který se vyvolá, pokud se vrátí hodnota HRESULT do modelu COM bez volání spravované metody.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 5dbfba2baec3263d91746c06379438e97a81f005
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051711"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
`invalidMemberDeclaration`Je aktivován pomocník spravovaného ladění (MDA), který nahlásí chybu, ke které dojde při určení způsobu zařazení parametrů člena, který se má volat z modelu COM.  
  
## <a name="symptoms"></a>Příznaky  
 Neúspěšná hodnota HRESULT se vrátí do modelu COM bez volání spravované metody.  
  
## <a name="cause"></a>Příčina  
 Nejpravděpodobnější příčinou je nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut u jednoho z parametrů.  
  
## <a name="resolution"></a>Řešení  
 Zadejte platné <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy pro parametry.  
  
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
