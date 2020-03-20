---
title: <appSettings> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155528"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="ddd9d-102">\<appSettings> \<element pro konfiguraci></span><span class="sxs-lookup"><span data-stu-id="ddd9d-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="ddd9d-103">Obsahuje vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-103">Contains custom application settings.</span></span> <span data-ttu-id="ddd9d-104">Toto je předdefinovaná konfigurační část poskytovaná rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="ddd9d-105">konfigurace &nbsp; &nbsp;>[\*\* \<\*\*](../configuration-element.md) \*\* \<aplikaceNastavení>\*\*</span><span class="sxs-lookup"><span data-stu-id="ddd9d-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ddd9d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddd9d-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="ddd9d-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="ddd9d-107">Attribute</span></span>

|           | <span data-ttu-id="ddd9d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ddd9d-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ddd9d-109">**Soubor**</span><span class="sxs-lookup"><span data-stu-id="ddd9d-109">**file**</span></span>  | <span data-ttu-id="ddd9d-110">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-110">Optional attribute.</span></span><br><br><span data-ttu-id="ddd9d-111">Určuje relativní cestu k externímu souboru obsahujícímu vlastní nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="ddd9d-112">Zadaný soubor obsahuje stejný druh nastavení, které jsou zadány v \*\* \<>sčítání **, \*\* \<odeberte>** a \*\* \<zrušte>\*\* prvky a používá stejný formát páru klíč/hodnota jako tyto prvky.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="ddd9d-113">Zadaná cesta je relativní vzhledem k hlavnímu konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="ddd9d-114">Pro aplikaci Windows Forms se jedná o binární složku (například */bin/debug*), nikoli o umístění konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="ddd9d-115">U aplikací webových formulářů je cesta relativní ke kořenovému adresáři aplikace, kde je umístěn soubor *web.config.*</span><span class="sxs-lookup"><span data-stu-id="ddd9d-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="ddd9d-116">Runtime ignoruje atribut, pokud zadaný soubor nelze najít.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ddd9d-117">Nadřazený prvek</span><span class="sxs-lookup"><span data-stu-id="ddd9d-117">Parent element</span></span>

|     | <span data-ttu-id="ddd9d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ddd9d-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ddd9d-119">\*\* \<konfigurační>\*\* Prvek</span><span class="sxs-lookup"><span data-stu-id="ddd9d-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="ddd9d-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ddd9d-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ddd9d-121">Child elements</span></span>

|     | <span data-ttu-id="ddd9d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ddd9d-122">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ddd9d-123">**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="ddd9d-123">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="ddd9d-124">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-124">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="ddd9d-125">**\<jasné>**</span><span class="sxs-lookup"><span data-stu-id="ddd9d-125">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="ddd9d-126">Vymaže všechna dříve definovaná nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-126">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="ddd9d-127">**\<odebrat>**</span><span class="sxs-lookup"><span data-stu-id="ddd9d-127">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="ddd9d-128">Odebere dříve definované nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-128">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ddd9d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddd9d-129">Remarks</span></span>

<span data-ttu-id="ddd9d-130">Prvek \*\* \<appSettings>\*\* ukládá vlastní informace o konfiguraci aplikace, jako jsou připojovací řetězce databáze, cesty k souborům, adresy URL webové služby XML nebo jiné vlastní informace o konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-130">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="ddd9d-131">Dvojice klíč/hodnota zadané v \*\* \<appSettings>\*\* element jsou přístupné <xref:System.Configuration.ConfigurationSettings> v kódu pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-131">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="ddd9d-132">Atribut **souboru** můžete použít v \*\* \<aplikaciNastavení>\*\* prvek konfiguračních souborů *Web.config* a aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-132">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="ddd9d-133">Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepíše nastavení zadaná v \*\* \<elementu>appSettings.\*\*</span><span class="sxs-lookup"><span data-stu-id="ddd9d-133">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="ddd9d-134">Atribut **souboru** lze použít ve scénářích vývoje týmu správy zdrojového kódu, například když uživatel chce přepsat nastavení projektu zadané v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-134">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="ddd9d-135">Konfigurační soubory určené atributem **souboru** musí mít kořenový uzel \*\* \<>nastavení aplikace,\*\* \*\* \< \*\*nikoli konfigurace>.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-135">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="ddd9d-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddd9d-136">Example</span></span>

<span data-ttu-id="ddd9d-137">Následující příklad ukazuje soubor nastavení externí aplikace *(custom.config),* který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="ddd9d-137">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="ddd9d-138">Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastaví vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="ddd9d-138">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ddd9d-139">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ddd9d-139">Configuration file</span></span>

<span data-ttu-id="ddd9d-140">Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd9d-140">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddd9d-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddd9d-141">See also</span></span>

- [<span data-ttu-id="ddd9d-142">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ddd9d-142">Configuration file schema for the .NET Framework</span></span>](../index.md)
