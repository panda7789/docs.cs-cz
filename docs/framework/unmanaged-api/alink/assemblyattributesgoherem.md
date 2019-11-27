---
title: AssemblyAttributesGoHereM – třída (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 15b9445aa3eabbd14541cfe5481bfb553c8c0347
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446629"
---
# <a name="assemblyattributesgoherem-class"></a>AssemblyAttributesGoHereM – třída

Používá se nástrojem ALink jako zástupný symbol pro ukládání informací o vlastních atributech.

## <a name="syntax"></a>Syntaxe

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a>Poznámky

Odkazy na tento typ mohou být vloženy do netmodule, jejichž zdroje obsahují vlastní atributy sestavení. Při sestavování manifestu sestavení z jednoho nebo více netmodule, které obsahují odkazy na tyto typy, nástroj ALink používá informace připojené k těmto odkazům k vygenerování skutečných uživatelských atributů. V takovém případě tento typ není nikdy vytvořen a odkazy na něj jsou používány pouze jako součást procesu sestavení a v konečném sestavení neslouží k žádnému účelu.

Odkazy na tento typ označují vlastní atributy, které nejsou související se zabezpečením, ale jsou vícenásobně použity.

Tyto typy jsou označeny jako "interní" v rámci .NET Framework a jsou umístěny v oboru názvů <xref:System.Runtime.CompilerServices>.

## <a name="requirements"></a>Požadavky

mscorlib.dll

## <a name="see-also"></a>Viz také:

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
