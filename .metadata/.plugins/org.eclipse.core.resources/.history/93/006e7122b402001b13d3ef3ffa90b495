package br.com.senai.av1.controller;

import java.util.Optional;

import javax.validation.Valid;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.ui.Model;
import org.springframework.validation.BindingResult;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.PutMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.ModelAndView;

import br.com.senai.av1.model.Usuario;
import br.com.senai.av1.repository.UsuarioRepository;

@RestController
public class UsuarioController {
	
	@Autowired
	private UsuarioRepository repository;
	
	@GetMapping("usuario/list")
	public ModelAndView findAll() {
		
		ModelAndView mv = new ModelAndView("/list");
		mv.addObject("usuarios", repository.findAll());
		
		return mv;
	}
	
	@GetMapping("usuario/add")
	public ModelAndView add (Usuario usuario) {
		
		ModelAndView mv = new ModelAndView("/add");
		mv.addObject("usuario", usuario);
		
		return mv;
	}
	
	@GetMapping("usuario/view/{id}")
	public String viewUsuario(@PathVariable long id, Model model) {
		model.addAttribute("usuario", repository.findById(id));
		return "usuario/view";
	}
	
	@GetMapping("/edit/{id}")
	public ModelAndView edit(@PathVariable("id") Long id) {
		
		return add(repository.findOne(id));
	}
	
	@GetMapping("/delete/{id}")
	public ModelAndView deleteById(@PathVariable("id") Long id) {
		
		repository.deleteById(id);
		
		return findAll();
	}
	
	@PostMapping("/save")
	public ModelAndView save(@Valid Usuario usuario, BindingResult result) {
		
		if(result.hasErrors()) {
			return add(usuario);
			}
		
		repository.save(usuario);
		
		return findAll();
	}
		
}


