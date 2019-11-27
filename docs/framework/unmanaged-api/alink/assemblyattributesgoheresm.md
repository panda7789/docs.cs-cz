---
title: AssemblyAttributesGoHereSM – třída (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
ms.openlocfilehash: 379ba20ebf675bec71e6e5f5bcfc0dc2fbd1f92c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446607"
---
# <a name="assemblyattributesgoheresm-class"></a>AssemblyAttributesGoHereSM – třída

Používá se nástrojem ALink jako zástupný symbol pro ukládání informací o vlastních atributech.

## <a name="syntax"></a>Syntaxe

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a>Poznámky

Odkazy na tento typ mohou být vloženy do netmodule, jejichž zdroje obsahují vlastní atributy sestavení. Při sestavování manifestu sestavení z jednoho nebo více netmodule, které obsahují odkazy na tyto typy, nástroj ALink používá informace připojené k těmto odkazům k vygenerování skutečných uživatelských atributů. V takovém případě tento typ není nikdy vytvořen a odkazy na něj jsou používány pouze jako součást procesu sestavení a v konečném sestavení neslouží k žádnému účelu.

Odkazy na tento typ označují vlastní atributy, které souvisejí se zabezpečením a vícenásobným použitím.

Tyto typy jsou označeny jako "interní" v rámci .NET Framework a jsou umístěny v oboru názvů <xref:System.Runtime.CompilerServices>.

## <a name="requirements"></a>Požadavky

mscorlib.dll

## <a name="see-also"></a>Viz také:

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
