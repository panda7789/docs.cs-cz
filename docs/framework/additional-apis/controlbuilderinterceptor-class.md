---
title: ControlBuilderInterceptor – Třída
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 312d977f832d262b1bebc6638280b67b133babdf
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88084393"
---
# <a name="controlbuilderinterceptor-class"></a>ControlBuilderInterceptor – Třída

`ControlBuilderInterceptor`Třída umožňuje proces kompilace přizpůsobit nebo řídit.

## <a name="syntax"></a>Syntax

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> `ControlBuilderInterceptor`Třída je interní a není určena pro použití přímo v kódu.
>
> Jak je popsáno v části poznámky, existence tohoto typu lze zkontrolovat a zjistit, zda je k dispozici podpora typu zachytávací. Společnost Microsoft v žádné situaci nepodporuje žádné jiné použití této třídy v produkční aplikaci.

## <a name="remarks"></a>Poznámky

V .NET Framework 2,0 a .NET Framework 3,5 aktualizace [ze srpna 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) přidala podporu pro použití typu zachytávací pro přizpůsobení nebo řízení procesu kompilace. Můžete určit, zda je tato podpora přítomna, pomocí nástroje <xref:System.Type.GetType?displayProperty=nameWithType> pro kontrolu existence `ControlBuilderInterceptor` typu, jak je znázorněno v následujícím kódu.

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

Pokud vrácená hodnota je jiná než null, je k dispozici podpora pro zachycování. Pokud je vrácená hodnota `null` , nebo pokud je vyvolána výjimka, pak aktualizace ze srpna 2020 nebyly nainstalovány a chybí podpora pro zachycování.

Pokud je k dispozici podpora pro zachycování, můžete napsat a zaregistrovat typ zachytávací, který bude komunikovat s procesem kompilace stejným způsobem jako <xref:System.Web.Compilation.ControlBuilderInterceptor> v novějších verzích .NET Framework. V .NET Framework 2,0 a .NET Framework 3,5 může být typ zachytávací libovolná třída, která splňuje následující požadavky:

* Má veřejný konstruktor bez parametrů.
* Má veřejné, nestatické metody s názvem `PreControlBuilderInit` a `OnProcessGeneratedCode` , které mají stejnou signaturu a sémantiku jako <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> metody a, které existují v novějších verzích .NET Framework.

Zaregistrujte typ zachytávací pomocí `aspnet:20ControlBuilderInterceptor` klíče v nastavení aplikace ASP.NET ( `<appSettings>` ). Toto nastavení aplikace musí být uvedené v počítači nebo v souboru aplikace *web.config* . Zadejte typ zachytávací pomocí kvalifikovaného názvu typu sestavení. Následující příklad ukazuje, jak zaregistrovat typ zachytávací s názvem `Fabrikam.Interceptor` .

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>

To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

Pokud je k dispozici podpora pro zachycování, proces kompilace spolupracuje s uvedeným typem způsobem popsaným výše. Pokud chybí podpora pro zachycování, nastavení aplikace se ignoruje a nemá žádný vliv.

## <a name="requirements"></a>Požadavky

**Obor názvů:** System. Web. Compilation

**Sestavení:** System. Web (v System.Web.dll)

**Verze .NET Framework:** 3,5, 2,0
