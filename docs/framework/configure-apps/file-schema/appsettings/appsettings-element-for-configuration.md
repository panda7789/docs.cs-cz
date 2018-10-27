---
title: '&lt;appSettings&gt; – element pro &lt;konfigurace&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 0ba57f51d3b1e78239677317933507ff009db035
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190928"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="675d3-102">\<appSettings > – element pro \<configuration ></span><span class="sxs-lookup"><span data-stu-id="675d3-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="675d3-103">Obsahuje vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-103">Contains custom application settings.</span></span> <span data-ttu-id="675d3-104">Toto je předdefinovaný konfigurační oddíl poskytuje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="675d3-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="675d3-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="675d3-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="675d3-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="675d3-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="675d3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="675d3-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="675d3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="675d3-108">Attribute</span></span>

|           | <span data-ttu-id="675d3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="675d3-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="675d3-110">**Soubor**</span><span class="sxs-lookup"><span data-stu-id="675d3-110">**file**</span></span>  | <span data-ttu-id="675d3-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="675d3-111">Optional attribute.</span></span><br><br><span data-ttu-id="675d3-112">Určuje relativní cestu na externí soubor, který obsahuje vlastní nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="675d3-113">Zadaný soubor obsahuje stejný druh nastavení, které jsou určené v  **\<Přidat >**,  **\<odebrat >**, a  **\<vymazat >** prvků a používá tyto prvky formátování stejného páru klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="675d3-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="675d3-114">Zadaná cesta je relativní vzhledem k hlavní konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="675d3-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="675d3-115">Pro aplikace Windows Forms, je to binární složka (například */bin/debug*), ne však umístění konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="675d3-116">Pro aplikace webových formulářů, cesta je relativní vzhledem k kořenový adresář aplikace, kde *web.config* se nachází soubor.</span><span class="sxs-lookup"><span data-stu-id="675d3-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="675d3-117">Všimněte si, že modul runtime ignorovat atribut, pokud zadaný soubor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="675d3-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="675d3-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="675d3-118">Parent element</span></span>

|     | <span data-ttu-id="675d3-119">Popis</span><span class="sxs-lookup"><span data-stu-id="675d3-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="675d3-120">**\<Konfigurace >** – Element</span><span class="sxs-lookup"><span data-stu-id="675d3-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="675d3-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="675d3-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="675d3-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="675d3-122">Child elements</span></span>

|     | <span data-ttu-id="675d3-123">Popis</span><span class="sxs-lookup"><span data-stu-id="675d3-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="675d3-124">**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="675d3-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="675d3-125">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="675d3-126">**\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="675d3-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="675d3-127">Vymaže všechny dříve definované aplikaci nastavení.</span><span class="sxs-lookup"><span data-stu-id="675d3-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="675d3-128">**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="675d3-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="675d3-129">Odebere nastavení dříve definované aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="675d3-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="675d3-130">Remarks</span></span>

<span data-ttu-id="675d3-131">**\<AppSettings >** element ukládá informace o konfiguraci vlastních aplikací, jako jsou databázové připojovací řetězce, cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="675d3-132">Páry klíč/hodnota zadaná v  **\<appSettings >** element jsou přístupné z kódu pomocí <xref:System.Configuration.ConfigurationSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="675d3-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="675d3-133">Můžete použít **souboru** atribut  **\<appSettings >** elementu *Web.config* a konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="675d3-134">Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepíše nastavení zadaná  **\<appSettings >** elementu.</span><span class="sxs-lookup"><span data-stu-id="675d3-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="675d3-135">**Souboru** atribut lze použít v týmu vývoje scénářích správy zdrojového kódu, jako je například, pokud uživatel požaduje přepsat nastavení projektu zadané v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="675d3-136">Konfigurační soubory, které jsou určené **souboru** atribut musí mít kořenový uzel  **\<appSettings >** spíše než  **\<konfigurace >**.</span><span class="sxs-lookup"><span data-stu-id="675d3-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="675d3-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="675d3-137">Example</span></span>

<span data-ttu-id="675d3-138">Následující příklad ukazuje soubor nastavení externí aplikace (*custom.config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="675d3-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="675d3-139">Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="675d3-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="675d3-140">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="675d3-140">Configuration file</span></span>

<span data-ttu-id="675d3-141">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="675d3-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="675d3-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="675d3-142">See also</span></span>

- [<span data-ttu-id="675d3-143">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="675d3-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
