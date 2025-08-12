# test-bee-mcp

Try different beeai-framework versions by changing it in the pyproject.toml

## beeai-framework==0.1.29 NO VALIDATION ERROR -- error is expected on API key because we have a bogus one

```shellsession
% uv add beeai-framework==0.1.29
% uv run src/tavily_mcp_tool.py     
Uninstalled 1 package in 33ms
Installed 1 package in 9ms
Tavily MCP server running on stdio
Tavily search failed: Search failed: Search failed: ToolError(beeai_framework.tools.errors): Tool Error
Context: {"name": "tavily-search"}
  McpError(mcp.shared.exceptions): Invalid API key
```

## beeai-framework==0.1.30 -- 2 validation errors because now time_range and country is required

```shellsession
markstur@Mac test-bee-mcp % uv add beeai-framework==0.1.30
Resolved 114 packages in 27ms
Uninstalled 1 package in 14ms
Installed 1 package in 7ms
 - beeai-framework==0.1.29
 + beeai-framework==0.1.30
markstur@Mac test-bee-mcp % uv run src/tavily_mcp_tool.py 
Tavily MCP server running on stdio
Tavily search failed: Search failed: Search failed: ToolInputValidationError(beeai_framework.tools.errors): Tool input validation error
Context: {"name": "tavily-search"}
  ValidationError(pydantic_core._pydantic_core): 2 validation errors for tavily-search
  time_range
    Input should be 'day', 'week', 'month', 'year', 'd', 'w', 'm' or 'y' [type=literal_error, input_value=None, input_type=NoneType]
      For further information visit https://errors.pydantic.dev/2.11/v/literal_error
  country
    Input should be 'afghanistan', 'albania', 'algeria', 'andorra', 'angola', 'argentina', 'armenia', 'australia', 'austria', 'azerbaijan', 'bahamas', 'bahrain', 'bangladesh', 'barbados', 'belarus', 'belgium', 'belize', 'benin', 'bhutan', 'bolivia', 'bosnia and herzegovina', 'botswana', 'brazil', 'brunei', 'bulgaria', 'burkina faso', 'burundi', 'cambodia', 'cameroon', 'canada', 'cape verde', 'central african republic', 'chad', 'chile', 'china', 'colombia', 'comoros', 'congo', 'costa rica', 'croatia', 'cuba', 'cyprus', 'czech republic', 'denmark', 'djibouti', 'dominican republic', 'ecuador', 'egypt', 'el salvador', 'equatorial guinea', 'eritrea', 'estonia', 'ethiopia', 'fiji', 'finland', 'france', 'gabon', 'gambia', 'georgia', 'germany', 'ghana', 'greece', 'guatemala', 'guinea', 'haiti', 'honduras', 'hungary', 'iceland', 'india', 'indonesia', 'iran', 'iraq', 'ireland', 'israel', 'italy', 'jamaica', 'japan', 'jordan', 'kazakhstan', 'kenya', 'kuwait', 'kyrgyzstan', 'latvia', 'lebanon', 'lesotho', 'liberia', 'libya', 'liechtenstein', 'lithuania', 'luxembourg', 'madagascar', 'malawi', 'malaysia', 'maldives', 'mali', 'malta', 'mauritania', 'mauritius', 'mexico', 'moldova', 'monaco', 'mongolia', 'montenegro', 'morocco', 'mozambique', 'myanmar', 'namibia', 'nepal', 'netherlands', 'new zealand', 'nicaragua', 'niger', 'nigeria', 'north korea', 'north macedonia', 'norway', 'oman', 'pakistan', 'panama', 'papua new guinea', 'paraguay', 'peru', 'philippines', 'poland', 'portugal', 'qatar', 'romania', 'russia', 'rwanda', 'saudi arabia', 'senegal', 'serbia', 'singapore', 'slovakia', 'slovenia', 'somalia', 'south africa', 'south korea', 'south sudan', 'spain', 'sri lanka', 'sudan', 'sweden', 'switzerland', 'syria', 'taiwan', 'tajikistan', 'tanzania', 'thailand', 'togo', 'trinidad and tobago', 'tunisia', 'turkey', 'turkmenistan', 'uganda', 'ukraine', 'united arab emirates', 'united kingdom', 'united states', 'uruguay', 'uzbekistan', 'venezuela', 'vietnam', 'yemen', 'zambia' or 'zimbabwe' [type=literal_error, input_value=None, input_type=NoneType]
      For further information visit https://errors.pydantic.dev/2.11/v/literal_error
```

## beeai-framework==0.1.35 -- 3 validation errors because above 2 plus now include_answer "extra" is not allowed

I think this actually started with 0.1.31.

```shellsession
markstur@Mac test-bee-mcp % uv add beeai-framework==0.1.35
Resolved 114 packages in 25ms
Uninstalled 1 package in 14ms
Installed 1 package in 7ms
 - beeai-framework==0.1.30
 + beeai-framework==0.1.35
markstur@Mac test-bee-mcp % uv run src/tavily_mcp_tool.py 
Tavily MCP server running on stdio
Tavily search failed: Search failed: Search failed: ToolInputValidationError(beeai_framework.tools.errors): Tool input validation error
Context: {"name": "tavily-search"}
  ValidationError(pydantic_core._pydantic_core): 3 validation errors for tavily-search
  time_range
    Input should be 'day', 'week', 'month', 'year', 'd', 'w', 'm' or 'y' [type=literal_error, input_value=None, input_type=NoneType]
      For further information visit https://errors.pydantic.dev/2.11/v/literal_error
  country
    Input should be 'afghanistan', 'albania', 'algeria', 'andorra', 'angola', 'argentina', 'armenia', 'australia', 'austria', 'azerbaijan', 'bahamas', 'bahrain', 'bangladesh', 'barbados', 'belarus', 'belgium', 'belize', 'benin', 'bhutan', 'bolivia', 'bosnia and herzegovina', 'botswana', 'brazil', 'brunei', 'bulgaria', 'burkina faso', 'burundi', 'cambodia', 'cameroon', 'canada', 'cape verde', 'central african republic', 'chad', 'chile', 'china', 'colombia', 'comoros', 'congo', 'costa rica', 'croatia', 'cuba', 'cyprus', 'czech republic', 'denmark', 'djibouti', 'dominican republic', 'ecuador', 'egypt', 'el salvador', 'equatorial guinea', 'eritrea', 'estonia', 'ethiopia', 'fiji', 'finland', 'france', 'gabon', 'gambia', 'georgia', 'germany', 'ghana', 'greece', 'guatemala', 'guinea', 'haiti', 'honduras', 'hungary', 'iceland', 'india', 'indonesia', 'iran', 'iraq', 'ireland', 'israel', 'italy', 'jamaica', 'japan', 'jordan', 'kazakhstan', 'kenya', 'kuwait', 'kyrgyzstan', 'latvia', 'lebanon', 'lesotho', 'liberia', 'libya', 'liechtenstein', 'lithuania', 'luxembourg', 'madagascar', 'malawi', 'malaysia', 'maldives', 'mali', 'malta', 'mauritania', 'mauritius', 'mexico', 'moldova', 'monaco', 'mongolia', 'montenegro', 'morocco', 'mozambique', 'myanmar', 'namibia', 'nepal', 'netherlands', 'new zealand', 'nicaragua', 'niger', 'nigeria', 'north korea', 'north macedonia', 'norway', 'oman', 'pakistan', 'panama', 'papua new guinea', 'paraguay', 'peru', 'philippines', 'poland', 'portugal', 'qatar', 'romania', 'russia', 'rwanda', 'saudi arabia', 'senegal', 'serbia', 'singapore', 'slovakia', 'slovenia', 'somalia', 'south africa', 'south korea', 'south sudan', 'spain', 'sri lanka', 'sudan', 'sweden', 'switzerland', 'syria', 'taiwan', 'tajikistan', 'tanzania', 'thailand', 'togo', 'trinidad and tobago', 'tunisia', 'turkey', 'turkmenistan', 'uganda', 'ukraine', 'united arab emirates', 'united kingdom', 'united states', 'uruguay', 'uzbekistan', 'venezuela', 'vietnam', 'yemen', 'zambia' or 'zimbabwe' [type=literal_error, input_value=None, input_type=NoneType]
      For further information visit https://errors.pydantic.dev/2.11/v/literal_error
  include_answer
    Extra inputs are not permitted [type=extra_forbidden, input_value=False, input_type=bool]
      For further information visit https://errors.pydantic.dev/2.11/v/extra_forbidden
```


