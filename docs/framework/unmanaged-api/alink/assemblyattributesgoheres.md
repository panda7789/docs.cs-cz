---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
ms.openlocfilehash: 128268bab77c8be5dc809eaa6d2548fc34f13cbd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446616"
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS

Používá se nástrojem ALink jako zástupný symbol pro ukládání informací o vlastních atributech.

## <a name="syntax"></a>Syntaxe

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a>Poznámky

Odkazy na tento typ mohou být vloženy do netmodule, jejichž zdroje obsahují vlastní atributy sestavení. Při sestavování manifestu sestavení z jednoho nebo více netmodule, které obsahují odkazy na tyto typy, nástroj ALink používá informace připojené k těmto odkazům k vygenerování skutečných uživatelských atributů. V takovém případě tento typ není nikdy vytvořen a odkazy na něj jsou používány pouze jako součást procesu sestavení a v konečném sestavení neslouží k žádnému účelu.

Odkazy na tento typ označují vlastní atributy, které souvisejí se zabezpečením a nejsou vícenásobně použity.

Tyto typy jsou označeny jako "interní" v rámci .NET Framework a jsou umístěny v oboru názvů <xref:System.Runtime.CompilerServices>.

## <a name="requirements"></a>Požadavky

mscorlib.dll

## <a name="see-also"></a>Viz také:

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
